---
title: "Switching all os's and need help!"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by krisarnold on 2009-10-15
Please help! Previously I had Vista and 9.04 in dual boot. I wanted to upgrade. Now I'm running windows7 64 bit and want to change my ubuntu to 64 bit. Since the upgrade to 7, Grub does not come up. How do I reload ubuntu using my previous ubuntu partition?

---

### Post by howefield on 2009-10-15
What are you running now, Windows 7 and Ubuntu 9.04 ?

When you install 64 bit Ubuntu, it will put grub back in it's place and pick up the other operating systems, it won't matter if you are putting 64 bit on as well as the other two, or instead of your current 9.04.

(Just to be clear, you can't "upgrade" your current 32 bit Ubuntu to 64 bit, you have to reinstall).

---

### Post by raymondh on 2009-10-15
+1

I think when you upgraded to win7, it overwrote the MBR and is now using the windows loader.

Since you plan to re-install 64-bit, GRUB will (once again) overwrite into the MBR and have you back dual-booting like before.  If you decide not to re-install Ubuntu and keep what you have, you will have to re-install GRUB.

Regards,

---

### Post by krisarnold on 2009-10-15
Yes. I cannot get into my current 32 bit 9.04. That is fine, as I knew I had to do complete re-install. My problem is that when attempting to install the new 64 bit, I want to put it exactly over the previous 32 bit partition. I am not sure how to do this. A side by side instalation leads me to believe windows 7, ubuntu 32 bit and ubuntu 64 bit.

---

### Post by raymondh on 2009-10-15
> **krisarnold said:**
> Yes. I cannot get into my current 32 bit 9.04. That is fine, as I knew I had to do complete re-install. My problem is that when attempting to install the new 64 bit, I want to put it exactly over the previous 32 bit partition. I am not sure how to do this. A side by side instalation leads me to believe windows 7, ubuntu 32 bit and ubuntu 64 bit.

You'll have to choose manual during the partitioning stage (step 4).  In manual, highlight the intended partition > edit > use as > set mountpoint > set format type

Back-up your files please.

Regards,

---

### Post by krisarnold on 2009-10-15
Ok. Thanks. Seems like I tried that and it showed the whole hard drive as one partition, I will try it again. Once again thanks for all the help

---

### Post by raymondh on 2009-10-15
If you are unsure about manual installations ... you can:

Boot into windows
Access the disk manager
Delete current ubuntu (leaving it free).  Note swap and extended partitions.
Boot into the Ubuntu liveCD
Install in continous free space

If you are still unsure about that ... you can:

Boot into windows
Access its' disk manager
Delete current ubuntu and its' swap and any extended partitions
Enlarge windows
Defrag windows
Boot into the Ubuntu liveCD
Install side-by-side (remember to use the slider)

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Regards,

---

### Post by howefield on 2009-10-15
Have a peek at the "Ubuntu Partitioning" video in this screencast, might help your understanding. (About the 4th video down the page)

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

