---
title: "Sylistic 4110 Display problems with gutsy"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by heathkit on 2007-10-27
I'm trying to install Gutsy on my Fujitsu ST4110 tablet and I'm running into a problem I've never seen before.  When X starts up, the screen is black.  It seems to be working properly, though, since I hear the startup sounds.  Every time I start X, although the screen is initially black, there are white patches or bars.  The longer I leave X running, the more the screen gets gradually whiter.  Occassionally, it will hard lock in this state.  When I kill the X server, I see some odd patterns (red rectangles, or other static or video noise ).  

The tablet has a built in Intel 8238 graphics adapter.  The driver it uses by default is intel, but I've tried vesa (exact same problem) and i810 (won't start).

It works fine under dapper, which just leaves me more confused as to what the problem might be.  I've tried running under dapper, but it seems that gutsy adds quite a few features that would make my life easier.  Anyone have an idea what the problem with gutsy is?

---

### Post by dewmagg on 2007-12-19
Has anyone found a solution to this?  I just installed Gutsy and I'm having the exact same problem...
Thanks in advance.

---

### Post by Paul.Spectre on 2008-04-11
I'm configuring a 4110 with Gutsy now, and I had the same symptoms until I changed the Device driver to "i810", now it works

---

