---
title: "reinstalling ubuntu-can't format root partition"
date: 2005-01-23
forum: Installation &amp; Upgrades
---

### Post by Leo Torjeman on 2005-01-23
hello,
   
 i have windows XP and ubuntu with dual boot, i just reinstalled my ubuntu system and when i try to format my hda3 partition as reiserfs (before it also was reiserfs) i get an failure, i tried to go to the terminal (ALT+F2) and run 
   mkfs.reiserfs /dev/hda3
   but i also get an failure, something about /dev/hda3 is not available, i get the same error when i try to run
   fdisk /dev/hda
   the error is that /dev/hda is not available
 i don't understand what happend, i worked excellent so far, i tried to install fedora 3 with reiserfs at those partition and it worked excellent. by the way i got the same error with ext3 fs.
   my partitions are:
   /dev/hda1-Windows XP
   /dev/hda2-swap
   /dev/hda3-Ubuntu
   
   how can i fix this?
   
   thanks

---

### Post by Leo Torjeman on 2005-01-23
the exact errors:
 
 # mkfs.reiserfs /dev/hda3
 stat of the device /dev/hda3 failed.
 
 # fdisk /dev/hda
 unable to open /dev/hda
 
 and from the ubuntu installer when trying to format /dev/hda3:
 
 the ReiserFS file system creation in the partition #3 of IDE1 master (hda) failed.

---

### Post by Leo Torjeman on 2005-01-24
someone?

---

