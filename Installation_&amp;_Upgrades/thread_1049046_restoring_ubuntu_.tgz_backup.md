---
title: "restoring ubuntu .tgz backup"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by matt91 on 2009-01-24
I have a backup from a few days ago which I am trying to restore to a different hard drive, I've created the partitions and tried to restore it however after installing GRUB I get "GRUB loading, please wait... Error 2".

The backup is exactly as it is on [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and I've tried restoring as it says, to the letter. I even did this twice to make sure.

I installed GRUB using the instructions on [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I am stuck as to where to go next, I've had an all night session and have got nowhere.

Thanks, Matt

---

### Post by matt91 on 2009-01-24
when installing grub "find /boot/grub/stage1" returns (hd1,0)

i run "root (hd1,0)" then "setup (hd1)" which completes with no errors.

The partition is recognised as sdb1. (my 3 raid drives taking sda,c,d)

I've checked the permissions of the extracted archive and it all seems to be in order.

Surely, I'm just missing something simple.

Any help would be greatly appreciated.

---

### Post by matt91 on 2009-01-24
Right, it seems this is not limited to restoring the backup. I decided to do a fresh install (for me to then copy over configs from the backup), I used the 8.10 disk and i get the exact error on boot up. Could it be something wrong with this hard drive (which is also an old one) or the SATA controller?

---

