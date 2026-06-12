---
title: "Grub help needed with 9.10 server"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by matt.martini on 2009-10-31
I have installed [COLOR=Blue]9.10 server[/COLOR] on a machine with SATA drives.  The install process goes well, yet after the initial reboot the machine just hangs.  I suspect that grub is not installed/working properly.  

I have tried this a number of times using different values when prompted for grub location.  The partition step (options: guided, entire disk, LVM, 10% of 250G) says that the main partition is ext4 on SCSI1(0,0,0) and that /boot is ext2 on partition #5 SCSI1(0,0,0).  

I have tried using hda, sda, SCSI1(0,0,0), and blank for the grub query.  All to no avail.  I even booted off the CD and said "boot off first drive" and still it just immediately hangs with a blinking cursor in the upper left corner (after BIOS screens).  (yes, the BIOS is set to boot off the SATA drive after CDROM)

Any help would be appreciated. 

Thanks

Matt

---

