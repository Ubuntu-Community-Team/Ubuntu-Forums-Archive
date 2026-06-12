---
title: "can someone help me configure xorg?"
date: 2011-03-15
forum: Hardware
---

### Post by ifyoushouldgoskating on 2011-03-15
Running Ubuntu 10.10, two ATI cards (one with 4 monitors, one with 2) for a total of 6 monitors. (using the normal radeon driver).  All monitors work fine, and display things, however, there are a couple issues.  Only one set of two monitors actually work in parallel (as opposed to being mirrored).  The other sets of two are mirrors of eachother and have their own menubars and taskbars (which is kinda weird).  When I go to the Monitors configuration gui thing, it acts as if there are two monitors, but it's different on each set of two.

Also, I'm looking at xorg.conf as it was by default… and it seems to think I have three graphics cards instead of two… and it only has three monitors/screens configured.  Every time i try to make a change (even changing the layout, such as changing "LeftOf" to "RightOf") the result is completely unpredictable.  Upon restarting the x server, a different set of two monitors are displayed properly, and the other two are mirrors…

Can someone please help?  I'm sorry if the explanation is confusing, the basic problem is configuring xorg.conf to properly use my 6 monitors (3x2 layout) with two graphics cards.

---

