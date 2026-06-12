---
title: "Persistent Live USB trouble"
date: 2008-08-18
forum: General Help
---

### Post by smvtsailor on 2008-08-18
As a complete Linux newb, this is my first attempt to install linux on something.  I've installed ubuntu onto a flash drive with the instructions [here]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/").  When I boot from the usb device, I can choose the "boot in persistent mode" option, and a window with "Loading Linux Kernel" and a percentage indicator pops up.  After about 20 min, it finally gets to 100% and then hangs.  What could be wrong here?  Thanks.

Sorry if this has been discussed before, I did try a search.

---

### Post by smvtsailor on 2008-08-18
just tried redoing everything, still the same problem.  Does anyone know what could be wrong?

---

### Post by smvtsailor on 2008-08-18
bump

---

### Post by smvtsailor on 2008-08-18
Does anyone know what could be wrong?  I've been trying to fix this for weeks.

---

### Post by randcoop on 2008-08-18
How big is the USB drive you're using (it should be at least 4GB)?

Did you try walking through the steps on pendrivelinux a second time?  Sometimes you get a command wrong (even a typo) and it will make it all fail.

Did you try to implement the lilo boot system that they mention at the bottom of the article?

What kind of hardware are you trying to boot?

The pendrivelinux approach should work for most computers, but there could be some issues with some hardware.  If you can't get Ubuntu to work, you could try Xubuntu (which requires less because it uses XFCE instead of Gnome) or even Puppy Linux, which is a much smaller distro and much less demanding of hardware.

---

### Post by smvtsailor on 2008-08-18
I am using an 8GB PNY flash drive.  I've tried the pendrivelinux method about 5 times, each time the same thing happens.  I have a common computer too- Dell Dimension 8300 with a pentium processor, so I doubt it is a compatibility problem.  I've tried lilo.  Its strange because I get to choose a language and select persistent mode, but then it just hangs after loading the kernel.

---

### Post by randcoop on 2008-08-19
There have been problems with pendrivelinux and Ubuntu installs with the initrd.gz file.  That file should be in your ubuntu8 partition in the casper directory.  But the instructions should have told you to delete the one that you get early in the process and then use wget to put a new version later on.  

Please be certain that you're using the right initrd.gz file.

---

### Post by smvtsailor on 2008-08-19
I'm using one that pendrivelinux indicated to use in the instructions.  Was there another specific initrd.gz that I should use?

---

### Post by smvtsailor on 2008-08-19
Would it matter that ubuntu8 is partition 2, casper-rw is partition 3, and there is a generic FAT32 partition in partition 1 for general flash drive use?  Would I have to modify vmlinuz or initrd.gz?  BTW, why is initrd a .gz?

---

### Post by randcoop on 2008-08-20
Indeed the partitions are probably your problem.  The boot process depends upon the location of the boot information and looks to the "first" partition to find it.  There's a way for you to use grub to change the default so that it looks in a different partition, but the pendrive approach is to use these two partitions in the order they tell you.

My guess is that your boot hangs because it's endlessly searching the wrong partition for the information it needs.

Incidentally, this is not a small difference.  When you post questions, you should try to provide as much information as possible.  You repeatedly said that you had followed the pendrivelinux instructions exactly, but those do not permit a third partition.  In fact, they specifically start by deleting any existing partitions.

---

### Post by smvtsailor on 2008-08-21
So, how would I modify initrd.gz (or the appropriate file) to look for this information in a specific partition?

---

### Post by randcoop on 2008-08-21
You don't modify the init file...you use grub to tell your computer where the file is.

I'm not expert in grub and so can't help you with this part of the problem, but there is considerable information on this forum and throughout the web on grub: how to add it to your system, how to designate specific partitions for finding the boot files, etc.  

Good luck.

---

