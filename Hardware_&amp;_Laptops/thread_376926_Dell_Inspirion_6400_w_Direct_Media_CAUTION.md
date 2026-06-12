---
title: "Dell Inspirion 6400 w/ Direct Media: CAUTION"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by Ocxic on 2007-03-05
on the inpirion, there is a hidden partition used for direct media, if after installing ubuntu your press this button, it will change the partion table entry on your hard drive of your first partition, in this cas my seperate /boot partiton, changed to the pervious windows partition.

What i did to fix this, is to just used fdisk from a live cd to change the partiton back to ext3 and all my data was still there and the computer booted normally, i just wish i hadn't spent an hour trying to install grub,onto an NTFS partition.

other then that everyhting seems to work well, havn't tried anything bluetooth yet tho, but wirs wokrs wonderfully, with minimal trouble shooting after we unpluged it from the lan and rebooted it, lol

---

### Post by Ek0nomik on 2007-03-05
The first thing I did when I got my laptop was knock out Windows and the Media Direct partitions.  That's another way to take care of it.  :)

---

### Post by halw on 2007-03-05
> **Ek0nomik said:**
> The first thing I did when I got my laptop was knock out Windows and the Media Direct partitions.  That's another way to take care of it.  :)

That's the best way.

---

### Post by Ocxic on 2007-03-06
i did the same thing, but pushing the media direct button is what caused the problem

---

### Post by weijie90 on 2007-03-26
After you push that damn button, the power button actually boots mediadirect.

Just reboot and press the mediadirect button again, and it will boot normally. After that, the power button returns to normal.

Mediadirect BSODs on me. ****

---

