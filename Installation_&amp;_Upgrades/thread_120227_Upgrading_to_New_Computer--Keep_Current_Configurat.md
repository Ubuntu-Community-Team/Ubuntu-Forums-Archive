---
title: "Upgrading to New Computer--Keep Current Configuration?"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by Greg T. on 2006-01-21
OK, so I'm about to upgrade to a new computer. New motherboard, video card, hard drives, the works. Of course, this typically requires a fresh install and tediously reconfiguring the new computer. Problem is, I've spent many, many, many hours getting my current configuration just right and don't want to start again from scratch. So I'm looking for alternatives.

I'm wondering if this would work:

(1) Install Ubuntu on the new computer, using the same version of Ubuntu as is on the old computer. (Just a basic install, no fiddling with settings after the installation is complete except as strictly needed.)
(2) Copy these files from the new computer and save them on a separate device (floppy, USB hard drive, etc.):

[INDENT]boot/grub/menu.lst
boot/grub/device.map
etc/fstab
etc/modules
etc/mkinitrd/modules
etc/X11/xorg.conf[/INDENT]

(3) Shut down the new computer.
(4) Transfer the handful files listed above to the old computer's hard drive, overwriting current files.
(5) Copy the contents of the old computer's hard drive to the new computer's hard drive, overwriting the contents on the new hard drive. (Note: I would not copy /proc, /lost+found, /mnt, or /sys.)
(6) Boot the new computer again and pray, dealing with (hopefully only minor) cleanup issues.

The idea is to use the files from old computer's hard drive (all my programs, customizations, etc.) in the new computer, except for any changes needed in configuration files to adapt to the new computer's hardware. I know I could figure out the details of some, if not all, of these files without first installing Ubuntu on the new computer, but the installation will prove that Ubuntu will actually run on the new hardware and also eliminate the possibility that I'd screw up these files if I'd tried to edit them by hand.

Presuming I do all the proper backups, I suppose I have nothing to lose other than an afternoon, but before I go any further on this I have to ask: Would trying to do this be a hopeless exercise? If not, any suggestions before I try?

---

