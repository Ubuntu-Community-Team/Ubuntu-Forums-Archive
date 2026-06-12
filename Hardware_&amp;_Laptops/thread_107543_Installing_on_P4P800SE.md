---
title: "Installing on P4P800SE"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by crouton on 2005-12-23
Had enough trouble with this that I thought I should post it up for other users in the same bind.

**Keywords:** 
P4P800 P4P800SE ICH5R IRQ18 irqpoll missing-modules

**Setup:**
System includes P4P800SE (or possibly any system that has the ICH5R chipset or exhibits this issue) and either/both PATA/SATA drives.

**Problem:**
Booting from Ubuntu 5.10 (Breezy Badger) installation CD, system will hang while loading CDROM drivers, then return with 'Cannot find CDROM device'.  Ctrl-Alt-F4 shows that several modules were 'missing'.  Ctrl-Alt-F2 and 'dmesg' shows a recommendation to use 'irqpoll' when booting, and that IRQ18 was ignored.

This is a bit tricky, as simply booting with 'linux irqpoll' did not solve the problem for me.  It would find the CDROM and progress further, but would hang at random points during the installation process.  Since I was installing to the PATA on /dev/hda (PATA) and my CDROM was also PATA (/dev/hdc), I went into the BIOS and set the IDE Chipset Configuration to 'Compatability Mode' with only PATA ports enabled.  Rebooting and using 'linux irqpoll' allowed me to complete the installation.  Once installation was completed, I reset the BIOS IDE Chipset Configuration to Enhanced mode, with PATA+SATA enabled.

N.B.!  You *must* edit your GRUB files to include 'irqpoll' on the '/kernel' line in order for any subsequent boots to work.  You can edit GRUB directly at boot, so long as you press 'b' to boot - hitting enter will boot without your changes.

If you are attempting to install to a SATA drive, there is an option when IDE Chipset Configuration is set to 'Compatability Mode' to use SATA plus (Primary PATA) or (Secondary PATA).  This should allow you to choose your CDROM drive based on its location and still follow the above instructions for installation.


I hope this is helpful for fellow Ubuntu users out there.  Please let me know if you have run into this issue and if this mini-guide helps.

Thanks!
-crouton

---

### Post by jeremy on 2005-12-24
I was interested to read this guide as I have installed ubuntu several times (warty, hoary & breezy) on a P4P800SE without any problems whatsoever. I have 2 SATA HDs, and 2 IDE CDs.

---

### Post by crouton on 2005-12-26
Would you mind explaining how you have your BIOS setup, then?  I'm curious to see if there's some sort of particular condition that must be met for such difficulties to occur.

Also, note that I did have PATA HDs present (and which I was installing to) which may have been the difference.

---

### Post by jeremy on 2005-12-27
Hello, I have all the default values in the BIOS, the only thing I did was to flash the BIOS to version 1006 (I think it was at 1004 whe I bought it).

---

### Post by Clefferson on 2006-03-22
Interesting..... with a P4P800 Bios version above 1006 [problems]("http://ubuntuforums.org/showthread.php?t=112626&highlight=asus+p4p800+solved") start to appear!

I'll try to downgrade my BIOS version to 1006.... hope it will work!:mrgreen:

---

