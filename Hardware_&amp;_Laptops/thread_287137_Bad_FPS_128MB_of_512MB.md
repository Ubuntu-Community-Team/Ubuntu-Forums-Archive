---
title: "Bad FPS? 128MB of 512MB?"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by illegalbuds on 2006-10-28
It looks like my FPS in fgl_glxgears is pretty low. I have an Acer Aspire 5670 with ATI Mobility Radeon x1400 512MB. Another thing, the video card memory only shows 128 of 512mb.
[[IMG]http://img48.imageshack.us/img48/2602/badfpszt1.th.png[/IMG]](http://img48.imageshack.us/my.php?image=badfpszt1.png)

---

### Post by tpg on 2006-10-28
If you haven't already, you could try installing the latest drivers from ati's website (version 8.29.6) here [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300). 

At [http://www.phoronix.net/forums/showthread.php?t=301](http://www.phoronix.net/forums/showthread.php?t=301) it suggests that you can get about 600FPS in fgl_glxgears using this driver from an x1400 .

I don't know about the memory issues, although maybe the fact that the x1400 shares system memory (I think) has something to do with it?

---

### Post by brouiller on 2006-10-28
The reason it says you only have 128mb of video ram is because, well, you only have 128mb of video ram, the reason you think you have 512mb is because they market the laptop as having "...up to 512mb with Hypermemory!" meaning that while the card only has 128mb of ram on it, it can use 384mb of your system memory as video memory. This slows down your card a lot and it's often better to run the card with Hypermemory disabled.

[wikipedia][Hypermemory]("http://en.wikipedia.org/wiki/Hypermemory")

---

