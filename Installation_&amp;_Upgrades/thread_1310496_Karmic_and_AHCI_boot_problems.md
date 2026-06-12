---
title: "Karmic and AHCI boot problems"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by iMat on 2009-11-01
HI All,

I've just done a fresh install of Ubuntu 9.10 on my laptop, Acer AS1410 and haven't been able to get it to boot with AHCI enabled in the bios..

The problem is I dual boot Windows 7, and switching ACHI to IDE will allow ubuntu to boot, but cause windows 7 to fail. Is there something I can do to get Ubuntu to boot with ACHI enabled?  I don't want to have to physically change between to get each one to boot..

During boot it stops at the following...

fsck from util-linux-ng 2.16
/dev/sda5: clean 127218/4890624 files, 852428/19543064 blocks
* Setting preliminary keymap..
* Starting AppArmor profiles
* Starting Kernal Oops catching servive kernaloops
* Speech-dispatcher configured for user sessions
* Starting Common Unix Printing System: cupsd
* PulseAudio configured for pre-user sessions
* Enabling additional executable binary formats binfmt-support
* Checking battery state...
   ...done.


Cheers

Mat

---

### Post by IgnorantGuru on 2009-11-01
In my experience with this on another machine, it was due to the chipset not being supported - hence no AHCI support.  So AHCI might not be an option.  I'm not familiar with Windows 7, but it seems strange it can't handle IDE.  I would look for a workaround for that.  The performance difference between AHCI and IDE is minimal in most situations.

---

### Post by IgnorantGuru on 2009-11-01
Actually it was the other way around - Ubuntu would boot with AHCI but not IDE, and WinXP would boot with IDE but not AHCI.  Regardless, in your case I think making Windows 7 accept IDE will be easier than making Ubuntu accept AHCI - just a hunch.

---

### Post by Pigcold on 2009-11-13
I switched to IDE mode before installing the Windows 7.

Then I installed the Karmic,

run the update manager,

And dual boot is working perfectly now.

---

