---
layout: post
title: Contract Programming
date: 13 Mar 2014 14:18:00
tags:
- delight
- release
- contract programming
- quoridor
---

**Edit:** Contract programming has been removed from Delight in favor of scope guards. If you really want it back in the language, let me know and we'll talk about it.

**Original:** I just succeeded in getting Quoridor to compile and run. Quoridor is now Delightful :) As a celebration, and because I found so many bugs in the process, I released a second beta. Hopefully we're nearing the version 0.1 release!

Besides all the bugfixes, I also added a few new features:

{% highlight D %}

function doit( int a, b -> int ):
enter:
	assert a less than b
exit result:
	assert result more than 0
body:
	return a / b

procedure main:
	auto arr = ["a": 1, "b" 2]
	assert arr has key "a"
	assert arr not has key "c"

{% endhighlight %}

The first method demonstrates [contract programming](http://dlang.org/dbc.html). I like this feature of D, since it is a clean way to ensure that the data the function takes and spits out are sanitary. Also, the code isn't compiled into a production version, meaning it shouldn't slow down performance either.

Another feature is the "has key" operator. This is used to check if an associative array has a certain key. In D this operator is called "in" but I'm already using that in the Python-esque way to check if an element exists in any kind of range-compatible structure.
