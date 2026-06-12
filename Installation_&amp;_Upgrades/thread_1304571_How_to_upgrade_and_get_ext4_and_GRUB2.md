---
title: "How to upgrade and get ext4 and GRUB2?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2009-10-29
I have a laptop that is running U9.04 in ext3 and I would like to install 9.10 as ext4 and with the new GRUB2.  I don't want to loose my data. What is a ;good way to go about this upgrade?  I don't have a tremendous about of data, so I could burn the files to a CD-R or CD-RW, or to several flash drives.  I am wondering about all the applications I have added over the last 6-months and my personal settings and such.  

So is there away short of a clean install to get the ext4 file system and GRUB2?

I have very few files on my Netbook so I think I could copy to flash drives or SD media cards and then do a clean install.  That is if I can update the USB flash drive that I used to install initially.

---

### Post by UNIXnewbie on 2009-10-29
Hi Jlh68,

It is easy to upgrade Ubuntu so I skip that.  To upgrade Grub, this worked for me [http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/](http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/)

It is also possible to upgrade ext3 to ext4: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by ssam on 2009-10-29
> **jlh68 said:**
> I have a laptop that is running U9.04 in ext3 and I would like to install 9.10 as ext4 and with the new GRUB2.  I don't want to loose my data. What is a ;good way to go about this upgrade?  I don't have a tremendous about of data, so I could burn the files to a CD-R or CD-RW, or to several flash drives.  I am wondering about all the applications I have added over the last 6-months and my personal settings and such.  

you have a backup of your data somewhere, right? at some point something will happen to your laptop or hard disk, so maybe today is a good day to do a backup.

i personally would not do a ext3->ext4 conversion with out my data backed up somewhere safe.

---

### Post by florus on 2009-10-29
You will not get the full benefit of ext4 unless you do a clean install.

---

