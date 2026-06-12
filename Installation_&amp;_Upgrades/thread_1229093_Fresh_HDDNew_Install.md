---
title: "Fresh HDD/New Install"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by okayneil on 2009-08-01
So guys, I got a brand new 500GB HDD. 

What Im wondering before going down the road on installing stuff is...in what order should I do things?

Id like to have Ubuntu + WinXpPro on 100GB each and the rest divided up into other partitions for file storage. 

Should I install Windowx first? Should I first partition everything with gparted?

What do you guys think is the best way?

yo

---

### Post by RJ12 on 2009-08-01
The best way is to install Windows XP first I dont know much of different hard drives but make sure when you install XP only have one HD plugged in otherwise it gets confusing.

---

### Post by merlinus on 2009-08-01
If you are wating to create a bunch of partitions, then using gparted, whether from its own live cd or the ubuntu one, might be best.  That way you can be certain in advance of your scheme.

You can create a primary 100G first, then an extended, and within that the others.

Then install xp into the first one, and install ubuntu.  You will have to select manual at the partitioning screen.

---

### Post by okayneil on 2009-08-02
I think im going to use gparted live cd...

so one partition formatted as ntfs, the other as ext3?

---

### Post by okayneil on 2009-08-02
bump!

---

### Post by merlinus on 2009-08-02
First primary formatted as ntfs, for installing windows.  Then an extended partition using all the rest of the space, and at least one ext3 partition within that for linux.  I highly recommend, however, that you set up a separate partition for /home, which is where application and personal preferences, configurations, email, bookmarks, and so on live.

Then when reinstalling, or installing a newer version of linux, it will remain untouched since you choose to use it but not to format it.

You can do this after installing windows whilst installing linux, however, from the partitioning menu

Also, you may wish to consider creating a logical ntfs partition, if you want to share data between both windows and linux.

---

