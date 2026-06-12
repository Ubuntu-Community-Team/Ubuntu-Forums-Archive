---
title: "How to install /home on a separate partition?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by okayneil on 2009-08-04
I've recently been informed that the best thing a person can do is to install /home directory on a separate partition, but how do you do that and is it worth it?

---

### Post by drs305 on 2009-08-04
To create a separate /home during installation, during Step 4 (partitioning) designate a separate partition and in the drop-down box for "Mount point" select "/home".

Here are a couple of links that explain how to move /home *after an install*:
Ubuntu Wiki:
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Other:
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html")

Having a separate /home partition can be advantageous if you plan on doing a clean install and wish to keep (most) of your user configurations. With an online update your user settings are mostly preserved whether you have a separate /home partition or not.

---

### Post by okayneil on 2009-08-04
So what your saying is yeah sure its kinda worth it but kinda not worth it.

---

### Post by drs305 on 2009-08-04
> **okayneil said:**
> So what your saying is yeah sure its kinda worth it but kinda not worth it.

It really depends on a lot of factors but comes down to personal preference. Many users highly customize their installations but prefer to do a clean install. They want to clean out old, unused apps, maybe use a different partitioning scheme, or even change from 32-bit to 64-bit. In such a case, having a separate home partition probably saves time and effort.

Others don't make many customizations or don't want to go through the trouble of installing a new release from scratch. For them, the value of having a separate home is probably not as great as for the first group.

So back to your quote, you are correct.  ;-)

---

### Post by tomasrey88 on 2009-08-04
Other poster couldn't answer your question because only YOU could answer your question. "Is it worth it" or not depends on what you want to do. If you want to upgrade in the future to Ubuntu 10.04 and if you want to keep all your settings (bookmarks, screensaver, etc), then yes, "It's worth it." However, if you like starting from scratch every time you upgrade, then, the answer is "no." Some people like starting from scratch every time to save hard drive space. 

Also, are you running a dual boot Windows and Ubuntu startup? If so, what version Win?

---

### Post by okayneil on 2009-08-04
> Also, are you running a dual boot Windows and Ubuntu startup? If so, what version Win?

Yes, how does that affect things?

---

### Post by tomasrey88 on 2009-08-04
Win98 is FAT32 so you only need primary partitions; / (root), /home, swap, and /windows.
However, if you have XP, then you'll need to make primary partitions and one extended partition (since you can only have 4 primary partitions); / (root), /home, swap, /fat32, /XP (ntfs). 

I answered your question. I invite you to look at my question: [http://ubuntuforums.org/showthread.php?t=1231361](http://ubuntuforums.org/showthread.php?t=1231361)

Thanks,
:P

---

### Post by merlinus on 2009-08-04
Also, windows will almost certainly not run if installed in anything but a primary partition.

---

