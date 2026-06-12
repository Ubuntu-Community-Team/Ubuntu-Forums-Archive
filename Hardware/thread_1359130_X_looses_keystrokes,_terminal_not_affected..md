---
title: "X looses keystrokes, terminal not affected."
date: 2009-12-19
forum: Hardware
---

### Post by TheKey84 on 2009-12-19
Hi,

I intalled Kubuntu Hardy on the laptop of my girlfriend, but the keyboard makes problems. It seems that X sometimes misses keydown- and keyup-events. So sometimes typed letters don't show and sometimes a typed letter repeats very often until I press it again (or another key). This bug makes it hard to get work done.

This problem occurs only in X, not on the terminl. I tried it an I'm sure. I also did the following: Opened Konsole and did "sudo cat /dev/input/event1" (which is the keyboard). I ran this in the background while typing on X, and I could see that the keystrokes where detected, but they didn't show on kate.

Is there a way to solve this or some kind of workaround?
Thanks for your help.

---

