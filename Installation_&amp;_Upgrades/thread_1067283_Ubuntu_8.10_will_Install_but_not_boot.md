---
title: "Ubuntu 8.10 will Install but not boot"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by hispeed120 on 2009-02-11
Hello all,

First of all, no more Windows for this guy, I'm done.  Anyways...

I'm trying to install Ubuntu 8.10 to my external hard drive and boot from it.  I would like to be able to take it anywhere and run Linux because it is fantastic.

Anyways, I am able to install 8.10 on the external HDD fine, but I am unable to boot from it.  I have disconnected my internal drive, so the external drive is the only one seen by the system.  I have also switched the boot order to boot from USB first.  My motherboard supports this action, so I cannot determine why I cannot boot from the external HDD.  I have performed the installation from a LiveCD that I got off of the website.  I have tried installing 8.10 before running from the LiveCD (Install Ubuntu) and from running Ubuntu from the LiveCD (try linux without changing your current settings).

Basically nothing comes up after I post; just a blinking underscore in the top left corner.  However, one time after an install (I've done about 10 installations on the external HDD now), I was able to start to boot 8.10, but was given "Error 25."  I have found things on "Error 21" but not "Error 25."

I'm not sure what I'm doing wrong.  The whole installation process is very straightforward, so I'm a little frustrated I cannot get it working.

Thanks in advance, and I'm glad to be a part of Linux now!!

---

### Post by jimv on 2009-02-11
There's a little trick you need to do during the install.  Click the Advanced button on the final screen before you actually start the install.  Set the GRUB to be installed to the USB drive.  Then, when you boot the computer, make sure you tell it to boot from the USB drive.

---

### Post by hispeed120 on 2009-02-11
I'm assuming the grub is the boot loader?  I have done this on the last step.  In the advanced tab, instead of defaulting to hd(0), I have it install the boot loader to sda1 (which is the external in my case, due to no internal connected).  Is this what you are talking about?

---

### Post by wpshooter on 2009-02-11
If you do NOT have anything on the external hard drive that you need to keep, then get [www.killdisk.com](www.killdisk.com) and WIPE that external drive completely clean and then try the installation again.  If it does not work from the live CD, then try installing from the alternate (text based) version.

---

