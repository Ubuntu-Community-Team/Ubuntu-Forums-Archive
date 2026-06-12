---
title: "Ubuntu 8.10 doesn't install on brand new SATA drive"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by CompSciSTL on 2009-02-28
I purchased a new SATA drive from the store yesterday and was going to install the 32-bit version of Unbuntu 8.10 on it.  I disconnected all other hard drives and plugged in the new drive.  My machine booted to the DVD drive as it should and I got the Ubuntu boot screen and I was able to select my language.  After that point it didn't seem to do much of anything.  The screen just went black and there was no other indication of the installation process happening.


When I first put in the Ubuntu CD, do I have to pick a special boot option to get the SATA controllers since I am trying to install the disk on a SATA drve?  Or should I go through the formatting metnioned in the Quick Formatting guide of the hard drive first?  (The drive came with a CD.  Never had to use one with other drives in the past...)

Here is my current system:
Q9450
Intel DX48BT2 motherboard
Western Digital 320GB Hard Drive (the newly purchased drive)
Samsung DVD/CD burner
4GB Kingston DDR3 1333 memory (2x 2GB)
MSI ATI Radeon 3870 Video card
X-Fi XtremeGamer sound card
Thermaltake 700Watt PSU

Any help is greatly appreciated!

---

### Post by MadAGu on 2009-02-28
maybe the disk hasn't burn right. Retry with another one....

---

### Post by auntiestacey on 2009-02-28
Ubuntu seems to be very touchy with sata drives. There are a few posts on the forums discussing it; you might have to search thru a few to find the right solution for you. One tip I can give you is to hit F6 on the install menu and add "pc=nomsi" (without the quotes) to the options line. That's how I got it to install on SATA drive after I upgraded from an IDE.

Now I'm trying to get it to install on a raid 0.....no luck yet.

---

### Post by CompSciSTL on 2009-02-28
I'll have to try that option auntiestacey.  I'll update my progress tomorrow.

---

