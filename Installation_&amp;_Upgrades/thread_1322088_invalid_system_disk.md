---
title: "invalid system disk"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by mykl on 2009-11-10
Have an ex-business 'puter that has been 'formatted' to erase all data. 2 x 20 gb hard drives and 512 + 256Mb of memory
 Have downloaded 9.10 and burnt a cd as image and configured bios to boot from cd. It runs through the startup and sees the two harddrives etc and'verifying dmi pool.....invalid system disk.
replace disk and then press any key.'
I have tried the alternative download and get the same result. The disk loaded ubuntu onto a windows laptop ok. Any pointers or suggestions what to do next?

---

### Post by Bartender on 2009-11-10
How fast did you burn the disc?  Was it a CD-R?
If this is an old PC with lots of miles on it, one of the easiest things to try might be popping the old optical drive out and slip in a newer one.  The old drive might be worn out and not able to hold tolerances.

---

### Post by coffeecat on 2009-11-10
This sounds like a BIOS message. Do you get 'Starting from CD..' or something similar before the 'invalid system disk'. Because, if not, it sounds as though it's trying to boot from the HD and obviously can't.

I know you said you configured the BIOS to boot from the CD, but it might be worth checking that your changes "took".

Or - you haven't got a blank floppy in the floppy drive, have you?

Last thought. It could be a dying CD drive since the CD seems to be OK.

---

### Post by mykl on 2009-11-13
Thanks to both of you for reply. No floppy drive, changed two different cd devices, and even tried with no hard drives connected, only booting from a knoppix minimal boot disk with no success. Borrowed from a very good friend two hard drives from a working box and it works ok, and am waiting for him to supervise the swapping of drives to get one of my drives set up as his slave and then install 'buntu on that and go from there. It has been suggested that perhaps the drives were swapped at the factory and duff ones put in. Anyway thanks again and looking to a successful install.:p

---

### Post by MrSnowmiss on 2009-11-13
Sounds like a corrupt MBR to me. You need a program called FixMBR (or similar) that can be found on a [HirenCD](http://www.hiren.info/) (among others).

---

