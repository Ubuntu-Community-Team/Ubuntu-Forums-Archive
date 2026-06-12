---
title: "unable to install ubuntu on sata hard disk"
date: 2014-10-10
forum: Hardware
---

### Post by uPatrick on 2014-10-10
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]0[/COLOR]down vote[favorite]("http://askubuntu.com/questions/534248/unable-to-install-ubuntu-on-sata-hard-disk/534569#")
[/CENTER]
[/TD]
[TD="class: postcell, bgcolor: transparent"]I would like to install lubuntu in my old pc. I have a pci sata/raid from Syba sa3114 which connect 3 sata hard disk 1TB When I install and create the partition, I recive the following message:
[SIZE=4]**The attempt to mount the file system with type ext4 in SCSI(0,0,0), partition#1 (sda) at boot fail**[/SIZE]
Does any one has problem with pci sata/raid cart ?
Here is my system info
-Computer-
Processor       : Intel(R) Pentium(R) III CPU family      1266MHz
Memory      : 1025MB (592MB used)
Operating System        : Ubuntu 14.04.1 LTS
User Name       : lubuntu (Live session user)
Date/Time       : Thu 09 Oct 2014 09:39:06 PM UTC
-Display-
Resolution      : 1440x900 pixels
OpenGL Renderer     : Unknown
X11 Vendor      : The X.Org Foundation
-Multimedia-
Audio Adapter       : VIA686A - VIA 82C686A/B rev50
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 ImPS/2 Logitech Wheel Mouse
-Printers-
No printers found
-SCSI Disks-
HL-DT-ST CD-RW GCE-8527B
HL-DT-ST DVD-ROM GDR8163B
ATA Hitachi HDS72101
ATA Hitachi HDS72101
ATA Hitachi HDS72101
[/TD]
[/TR]
[/TABLE]

---

### Post by weatherman2 on 2014-10-10
That old computer needs to be able to boot off of a device attached to a PCI card.  This isn't always possible on old computers.  But you can check in the BIOS for options on booting e.g. "boot other device."

If it's not possible to boot from a SATA drive connected to a PCI card, your next best option may be to boot from an old PATA/IDE drive - just put your /boot partition there and put everything else on the SATA drive.  You could put Grub on a floppy drive as well but I'm not sure you'd be able to boot then to the SATA drive.  There's probably not enough space for /boot on a 1.44MB floppy drive.

---

### Post by uPatrick on 2014-10-10
it is posible i will hAve APROBLEM ON BOOT ON PCI SaTA.
aCTUally , i hAve APROBLEM TO INSTaLL UBUNTU ON saTA DISK.
IS THERE THE DRIVER ISSUE ON UBUNTU ?

---

