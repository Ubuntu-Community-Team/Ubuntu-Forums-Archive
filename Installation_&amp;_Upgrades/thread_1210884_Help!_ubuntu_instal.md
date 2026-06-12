---
title: "Help! ubuntu instal"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by 220010497 on 2009-07-12
Well i love ubuntu but i love vista. but vista eats to much drive. so i got a separate drive that i want to use for ubuntu and its an internal drive. but i was wundering. when GRUB installs, when i remove the ubuntu hard disk and put in my vista will grub still be there loged into the bios or will it just be by its self on the other hard drive.???

---

### Post by earthpigg on 2009-07-12
someone else please re-read what i am about to type and verify that it makes sense. 2201, dont do this until a few people say that my unconventional solution will indeed work.

leave windows installed on first internal hard drive.

install ubuntu on 2nd hard drive, and have it take up the entire thing.

then, do an ubuntu minimal command line install on the first internal hard drive on a 1 gig partition.

ubuntu minimal will detect the windows and main ubuntu install, and make appropriate GRUB entries.

if the main ubuntu hard drive is removed, the ubuntu minimal grub will still be able to load windows like normal.

trying to boot main ubuntu when the hard drive is removed will obviously result in error.... but plug it back in, and it will work again right away without having to change anything.


i know this is not the most *_efficient_* way to do this, but its probably the easiest, and unless 2201 is hurting for hard drive space (and it sounds like he has plenty), he wont miss the 1gig. _**will this work?**_

edit:

smoked a cig and considered disadvantages of this method:

our little mini grub install wont include updated kernels, or ubuntu 9.10 if/when he installs that. easiest way around this is to reinstall our ubuntu minimal install once every 6 months.

2201: the alternative is to manually edit the grub. this will involve either learning the inns and outs of grub, or visiting ubuntuforums.org every 6 months. this solution, as i said, is by far *_not the most efficient_*, but it will save you the trouble of doing that.

---

### Post by coffeecat on 2009-07-12
**220010497**, I'm not clear exactly what you mean.

Do you mean that you are going to physically remove the Vista hard drive and replace it with the new drive to install Ubuntu? And also that you will only ever have one drive in the machine - either Vista or the Ubuntu one? Then, yes, that will work because all of grub will be on the new drive with Ubuntu and the Vista drive will still have its own Windows bootloader.

But if you mean that you are going to put the new drive in as the **second** drive on which to install Ubuntu, (leaving the Vista HD in the machine) and then remove it whenever you want to run Vista then, no, that won't work.

But back to the first option. If you intend to repeatedly swap the two drives, be aware that the connectors (particularly SATA ones) can be easily damaged. Think about getting yourself a removable hard-drive caddy casing and two caddies. The casing goes in a spare optical drive bay and has much more robust connectors than the actual drives. This is how I started out with Linux - at least until I was confident enough to know how to reinstall grub and/or repair the Windows bootloader.

---

