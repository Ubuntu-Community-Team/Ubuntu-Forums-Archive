---
title: "Best file system for old laptops?"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by benton on 2007-10-10
Hi there, I'm going to install Xubuntu 7.10 on a 1Ghz Pentium III laptop, with 384MB of RAM and a slow 30GB HD. I believe ext3 "wastes" some space, i.e., will use more space than it really needs. I don't care a lot about loosing information on that laptop, I just want it to be "fast" while accessing the HD. Any thoughts?

Thanks,

-Benton

---

### Post by atlfalcons866 on 2007-10-10
i use jfs. It is fast and reliable. I have had a couple power outages with and i havent lost any data. JFS also uses less cpu than ext3. JFS dosent fsck itself after 30 mounts like ext3. JFS stands for Jorunaled FIle system.

---

### Post by notwen on 2007-10-10
[ReiserFS]("http://www.namesys.com/") is fast as can be, but development is kinda at a stand-still since it's creator is being charged w/ the murder of his wife.  You should check it out, the FS that is. =]

---

### Post by Linicks on 2007-10-10
Use ext3 - it _is_ a journalled file system, is old and mature and rock solid.

Nick

---

### Post by benton on 2007-10-11
> **atlfalcons866 said:**
> i use jfs. It is fast and reliable. JFS dosent fsck itself after 30 mounts like ext3.

Hey, I actually like that! :) It gives me peace of mind. Seems that I'll have to learn how to schedule fsck runs. Anyway thanks for the tip, I'll try JFS as soon as Xubuntu Gutsy gets released.

Cheers,

-Benton

---

### Post by notwen on 2007-10-11
> **benton said:**
> Hey, I actually like that! :) It gives me peace of mind. Seems that I'll have to learn how to schedule fsck runs. Anyway thanks for the tip, I'll try JFS as soon as Xubuntu Gutsy gets released.

Cheers,

-Benton

[Bonager]("http://ubuntuforums.org/showthread.php?t=295262") is a utility that lets you know how many reboots before fsck is going to be ran and also lets you post-pone fsck.  You may wish to look into it should you settle on ext3. =]

---

### Post by Linicks on 2007-10-11
I don't know what the adversion to ext3 fsck is?  It doesn't harm anything (in fact it is designed to keep file system tip-top), and stopping it/changing the schedule can be related to ignoring a mileage oil change in your car.

Nick

---

### Post by notwen on 2007-10-11
> **Linicks said:**
> I don't know what the adversion to ext3 fsck is?  It doesn't harm anything (in fact it is designed to keep file system tip-top), and stopping it/changing the schedule can be related to ignoring a mileage oil change in your car.

Nick

A file system check on a 160gb HDD on a laptop which reboots.. more than your average desktop, would get to be bothersome should a 30min fsck popup when you need immediate access to your laptop.  =]

---

### Post by Linicks on 2007-10-11
It would be even more bothersome if the disk failed due to corruption...  and remember, laptops are more prone to disk errors than another system[s], due to the very nature of being mobile, bumped, shutdown wrongly etc.

Nick

---

### Post by theBuggane on 2007-11-05
regarding fs check frequency, see the tune2fs utility, ie. man tune2fs to find out more...

---

