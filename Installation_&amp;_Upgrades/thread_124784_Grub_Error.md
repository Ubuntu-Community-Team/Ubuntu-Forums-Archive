---
title: "Grub Error"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by jonathanm on 2006-02-02
Hiya, i have been trying to install Ubuntu onto my sisters computer for her and have had a few problems:

First there was the endless loop of adduser (that only came up on the first install though so it should be okay)

Then halfway through everything was installed there was a grub error 17.  After googling it it sems that it was a problem with grub not being able to mount the partition.

Reinstalled Ubuntu (going on 5 times now with different discs and tried changing the boot partition from ext3 to ext2, changed but no difference, then put the grub onto the boot partition instead of the mbr, still no difference)

I have checked the menu.lst file and there does not seem to be anything wrong.  So i can boot into knoppix and check the system but not an os on the hd.

By the way, i am trying to dual boot Ubuntu and win98.

Heres my version of whats on the partition table:

hda1     3Gb       fat32      win98
hda2     32Mb     ext2       boot
hda3     512Mb   swap      swap
hda5     1.3Gb    reiserfs   root
hda6     0.9Gb    fat32      docs


This is not my comp it is a 322Mhz P2 Deschutes ~6Gb so ignore my sig

thanks

---

### Post by taurus on 2006-02-02
What does your /boot/grub/menu.lst look like anyway?

---

### Post by jonathanm on 2006-02-02
well im not at the comp at the moment but from what i can remember its:

##################################

#normal options

## Begin Debian Magic Stuff##
Ubuntu, kernel 2.6.9-27 (or something similar)
root = hd(0,1) ro,usplash, 

Ubuntu Recovery
root = hd(0,1) single

## End Debian AutoMagic ##

This is a divider inserted by Debian

Win98 Chainloader
root = hd(0,0)
chainload

#############################

or something similar

when i get home i'll see if i can post the proper one

thanks

---

### Post by taurus on 2006-02-02
You are missing two important lines after the root thing, one for kernel and one for initrd.  So, post your complete /boot/grub/menu.lst when you get a chance...

---

