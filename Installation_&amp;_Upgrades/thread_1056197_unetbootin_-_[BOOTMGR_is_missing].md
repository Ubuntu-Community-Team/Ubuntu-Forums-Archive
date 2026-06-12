---
title: "unetbootin - [BOOTMGR is missing]"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by jimmyboy09 on 2009-01-31
Hi there.  I wanted to install ubuntu for a dual boot (w/ xp) on my laptop, but didn't want to burn the iso file to a disc.  So I used UNETBOOTIN with a downloaded iso file.

     The extraction to my 320gb usb drive worked out fine, and I rebooted, selecting to boot from usb drive.  Only problem is, I get the message: "BOOTMGR is missing.  Press Ctrl Alt Del to restart."

     For what it's worth, I also already tried Wubi, and that didn't turn out well either ("BUG...soft lockup...61s!").

     Any help would be greatly appreciated.

---

### Post by pedrogent on 2009-01-31
> **jimmyboy09 said:**
> Only problem is, I get the message: "BOOTMGR is missing.  Press Ctrl Alt Del to restart."

i'd also appreciate any help in this regard...

---

### Post by not a pipe on 2009-03-26
I had this problem while trying to triple boot xp, vista, ubuntu. Solved it by copying the files that were missing into xp. Not sure if that's the solution here, but it may be worth looking into.

The thread on this is around here somewhere. (wish I could find it)

---

### Post by Ad Avis on 2009-06-14
Format the drive as FAT (not FAT32)

Only thing that fixed it for me. Also make sure the partition on the disk is active see [HowToGeek - Create a bootable USB]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")

---

### Post by Hoodline on 2009-06-14
i am actually having this problem now but i am going to stick with ubuntu for 
a while and fix windows somehow if i get bored of ubuntu

i think the best thing about ubuntu is that is comes with programs you would use and keep
unlike windows coming with programs you proberly wouldnt use or you dont want

---

### Post by kuric on 2011-09-28
Old topic but I had this issue recently.
I used a pen to install windows 7, it was formatted to ntfs.
Then I used the same pen with netbootin to install ubuntu.
Stupid me. Of course, bootmgr was missing.
So, all I had to do was format the pen to fat32.

---

### Post by JigglyWiggly_ on 2011-10-20
> **kuric said:**
> Old topic but I had this issue recently.
I used a pen to install windows 7, it was formatted to ntfs.
Then I used the same pen with netbootin to install ubuntu.
Stupid me. Of course, bootmgr was missing.
So, all I had to do was format the pen to fat32.

A big thanks :popcorn:

---

