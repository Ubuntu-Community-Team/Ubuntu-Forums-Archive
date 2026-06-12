---
title: "GRUB Error 17"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by picardo on 2009-06-04
heya,

I used to have a partition housing Ubuntu. When I installed Wubi, I deleted that partition. Now when the operating system starts I see this error. What can I do?

---

### Post by Therion on 2009-06-04
This thread might help:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by picardo on 2009-06-04
> **Therion said:**
> This thread might help:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

That was kind of useful. But I cannot find the device.map file anywhere on the computer. 

Here is what I did. I made it bootup from  the USB. I looked around and discovered there are 4 disks that can be mounted. disk-1 is evidently the USB bootup disk. disk-2 is the drive that contains Windows and Wubi Ubuntu, which means it doesn't have a GRUB folder. disk-3 is where I used to have Ubuntu partition before I deleted it. Now there is nothing there, except for an empty file. 

Where is this device.map that controls my bootup sequence even though it's not anywhere I can see? 

PS: I recall seeing another primary partition which I couldn't find from the live USB disc. I assume it was a small PE partition. I didn't touch that. The file could be in there, but how do I get there if I cannot find it?

---

