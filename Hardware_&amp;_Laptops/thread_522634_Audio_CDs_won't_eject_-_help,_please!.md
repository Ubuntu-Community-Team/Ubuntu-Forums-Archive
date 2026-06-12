---
title: "Audio CDs won't eject - help, please?!"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by myke on 2007-08-10
Help, please!?

I can't get my audio cds to eject without manually pushing the button on the laptop or on my external player.  What is odd is that no matter what type of disk I put into either the internal or external player (cdr, cdrw, dvd, etc), they all mount and are read fine (including audio cds).  However, the only ones that will not eject through KDE are audio CDs.   It doesn't matter whether I try the menu that pops up when right clicking on a desktop icon or whether I use the menu from the storage media panel applet ... the result is the same.  Whenever I highlight the "eject" option, it gives the following error:

"error - kio_media_mount helper

audiocd:/ cannot be found"

This has only been occuring for about the last week so I can not figure out what causes it.  The audio cds are mounted, read, and can be played through any media player I try ... it's just that they will not eject using KDE versus manually pushing the eject button directly on the drives.   This is quite a pain in the backside especially as any other cd/dvd will eject properly.    

Only audio CDs seem to be affected.  Can anyone PLEASE help?  Is there something in fstab or mtab or some other place I should check that might be corrupted or have an error?  All drives are working properly and read anything properly ... there's just this majorly annoying unable to eject audio CDs problem.

Any help or suggestions would be greatly appreciated!!

---

### Post by aysiu on 2007-08-11
I'd file a bug report, even though [it doesn't appear to be happening for too many other users](http://www.google.com/search?num=100&hl=en&safe=off&q=%22audiocd%3A%2F+cannot+be+found%22&btnG=Search).

Have you tried creating a new test user and seeing if the test user runs into the same problem (make sure that test user belongs to all the proper user groups)?

---

### Post by Rebel Dragon on 2007-12-05
I'm having the same issue.

---

