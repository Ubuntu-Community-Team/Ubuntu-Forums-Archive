---
title: "Not seeking floppy on bootup after installation"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by Skote1 on 2005-05-12
I'm fairly new to Linux & recently installed Ubuntu several weeks ago.  Anyways I've come across a problem trying to boot up off of a floppy disc using an old win 98 bootup disc.  My bios is set right and my floppy drive is cycling on startup.  When the GRUB menu comes up, instead of seeking the floppy drive it goes directly into Ubuntu bootup.  I know it is probably something simple, and would really appreciate any help.  Sorry if this is the wrong forum for this.

Thanks,
Scott

---

### Post by nad on 2005-05-12
If your win98 boot disc is set to boot before your hard drive, you will not see the grub menu.

Check the boot disc for a valid boot sector.

---

### Post by Skote1 on 2005-05-13
Thing is I'm not trying to get into GRUB.  The computer isn't even attempting to boot off the floppy upon bootup.  The floppy does cycle when the computer is intially turned on, but where it should attempt to read the floppy for boot the computer doesn't even make an attempt to read off the floppy.  I have checked my bios too.  I am wonder if it could be something with my mbr?  Even since I've had this computer I haven't been allow to bootup from the cdrom either(& it does have the cdrom option in bios).  The floppy bootup problem just started after installing Ubuntu. BTW the computer has an old Celeron overclocked to 400 MHz on a ABIT BH-6 motherboard.  Thanks for any help.

Scott

---

### Post by nad on 2005-05-13
The mbr is in the first sector of your hard drive. Once again, I suspect either the floppy disk or the drive itself. Both are notorious for failure. Will the disk boot another computer? Will a fresh boot disk work in your computer?

Bios' often have unsupported options in them. A manufacturer will purchase code for a line of motherboards and not bother to modify it for boards with less support.

---

