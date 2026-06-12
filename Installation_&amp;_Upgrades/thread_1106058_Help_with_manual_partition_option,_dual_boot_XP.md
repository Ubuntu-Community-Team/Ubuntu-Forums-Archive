---
title: "Help with manual partition option, dual boot XP"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by jkwi on 2009-03-25
I may be missing a simple, key piece of info on the 
 installation. Probably making this harder than it needs
 to be. 

 How do I force the ubuntu installation to a certain partition?

 Have
 120GB HD 
   8GB FAT32 recovery
   112GB NTFS XP  boot

 Used LiveCD and gparted to resize and create:
   8GB FAT32 recovery
   80GB NTFS XP  boot
   13GB Primary  ext3, label /
   Extended 19GB
      15GB ext3  label /home
       4GB swap

 When I do the install, guided partition option still wants to 
 break up my NTFS for the ubuntu.
 If I choose manual option, I'm confused on where the install
 is going. None of the guides I've seen go into this manual 
 option. Is the / label enough to force the install there?
 I don't want ubuntu messing with my XP NTFS partition.

 Thanks for any help.

---

### Post by cariboo on 2009-03-25
Use the manual partitioning option during installation to specify the partitions you want to use. No need to force anything. Choose the partitions you want to use and mark them for formatting. Just in case make sure you have backed up all the important files on your Windows partition.

Jim

---

### Post by rjl6591 on 2009-03-25
> **jkwi said:**
> Is the / label enough to force the install there?
 
Yes. / means the 'root partition', and that's where Ubuntu will be installed.

---

### Post by jkwi on 2009-03-30
Thanks, that's what I needed to know. Obvious I guess, but I 
wasn't sure.

---

