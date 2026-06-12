---
title: "[Intrepid] Mouse click stops working"
date: 2008-11-08
forum: Hardware
---

### Post by zackiv31 on 2008-11-08
I saw this in the Intrepid Beta forums but couldn't post there...

At random times I get lockups with Intrepid and my mouse doesn't allow me to "click" tried multiple mice (all USB... one wired, one wireless, and one bluetooth)  none of them are responsive.

The mouseover aren't even recognized, but the mouse moves freely around... I can still operate everything normally through the keyboard, but this unfortunately is not the solution I'm looking for.  Anyone else seen these issues?

---

### Post by mgangav on 2008-11-09
Yeah, I've got about the same issue. Some times, my mouse just dies randomly. But, I've got a touchpad, so I can still move the pointer. Why is this happening?

---

### Post by John Jason Jordan on 2008-11-09
There appears to be a duplicate thread on this matter:

[http://ubuntuforums.org/showthread.php?p=6141563#post6141563](http://ubuntuforums.org/showthread.php?p=6141563#post6141563)

I know I solved this problem over a year ago, but I can't remember how. I am searching my old posts to see if I can locate the thread.

---

### Post by John Jason Jordan on 2008-11-09
OK, y'all, I finally found where I had discussed this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

If you read the entire thread you will find various possible solutions.

---

### Post by DaveSuffling on 2009-01-30
Confirmed the solution posted there. To paraphrase: 

Use alt-space to see which monitor is active. (A menu will appear on one monitor; that monitor is the active monitor.) 

Use alt-tab to select a window on the active monitor. 

Use alt-space, M to move that monitor. 

Press an arrow key to bind the mouse to that window. 

Move the mouse across a monitor/monitor boundary and click to release the window. 

This should resolve the problem. 

--DS

---

### Post by naroom on 2009-03-16
Wow, that's hilarious. But it worked! Thanks!

---

