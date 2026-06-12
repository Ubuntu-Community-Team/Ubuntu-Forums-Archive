---
title: "Strange External hard disk problem!"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by Roytheboytoy on 2007-05-15
Hi,

I am having a very weird experience with feisty right now. I have an external 250 GB external hard disk (Freecom). This hard-disk does not have an on-off switch... It turns on automatically when plugged in. It has 3 non-linux partitions on it. 

Now, I recently installed feisty, and on the live CD, the hard disk ran perfectly. When I installed feisty locally, The hard disk failed to detect at all. When I ran the Live CD again, it still did not work. Strangely enough, Its like the the USB port itself gets "turned off" when initial trials to mount the disk fail. Switching the disk off and on has no effect. i.e. ubuntu doesn't even try to detect the disk again. I did get an error a few times  (not always) that "HAL failed to load" when ubuntu started up.

I have looked at the post below and it has not helped.
[http://ubuntuforums.org/showthread.php?p=2643893](http://ubuntuforums.org/showthread.php?p=2643893)

What's really wierd is that when i flip in the live CD of Dapper, everything works perfect there! 
Hard-disk detects with no problem. I have a Dell D600 laptop.


Can somebody please please help me!

---

### Post by Ken_Lewis81 on 2007-05-15
My suggestions:

Connect your drive and type 'lsusb' in a Terminal Window.  That should trigger the automounter.

Then we need to find a way to have the system recognise what's happening.  It may be that HAL is broken and the fastest way to fix that is to file bugs and information about your system in Launchpad.net (for Ubuntu) and at bugs.freedesktop.org (for the people who supplied HAL to Ubuntu).  I suggest you tell Ubuntu that HAL works on the LiveCD but fails after install.

Take care.
Ken.

---

