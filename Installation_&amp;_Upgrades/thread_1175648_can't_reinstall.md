---
title: "can't reinstall????"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by blastbar on 2009-06-01
hi everyone, yes its another one of my daft posts =[
    i want to reinstall ubuntu 9.04, currently its the only thing on my system but when i try and boot from the disk it just comes up as the normal screen.   The disk image and all files are there on the desktop so my computers reading it but i just cant boot from it. 

   any help or clues??? much appreciated    Blastbar

---

### Post by pricetech on 2009-06-01
Maybe your BIOS is set to boot to the Hard Drive before the Optical.  You should have an option at boot time to open a menu which allows you to change the boot order for a single boot.  Alternately you can change the boot order in the BIOS and either leave it that way or change it back when you're done.

Just a thought.

---

### Post by blastbar on 2009-06-01
the message that comes up at the start that says press escape for menu and gives you 3 seconds?

---

### Post by blastbar on 2009-06-01
pressed escape and got
ubuntu 9.04, kernel 2.6.28-12-generic
ubuntu 9.04, kernel 2.6.28-12-generic (recovery)
then those same 2 options again
and one that says ubuntu 9.04, memtest86+

in recovery menu:
resume,      normal boot
clean,          free space
dpkg,           repair broken packages
fsck,            file system check
grub,           update grub bootloader
netroot,       drop to root shell prompt with network
root,            drop to root shell prompt
xfix,             auto repair graphic problems

---

### Post by blastbar on 2009-06-01
any ideas?

---

### Post by pricetech on 2009-06-01
> **blastbar said:**
> the message that comes up at the start that says press escape for menu and gives you 3 seconds?

Nope, before that.  You're looking for a menu that appears when your computer first boots, before it attempts to load anything.

---

### Post by blastbar on 2009-06-01
oooh yeah found it now thanks for all replies i reinstalled but still having problems
   thanks again to you again pricetech,    blastbar

---

### Post by blastbar on 2009-06-01
hiya yeah more problems now when ever i put anything in teminal i get this:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

 any help?

---

