---
title: "USB ports not working with flash drives and external drives"
date: 2009-01-14
forum: Hardware
---

### Post by Macfunky on 2009-01-14
I have recently gotten my hands on an old desktop and upgraded a few things on it and installed Ubuntu. Basically the USB ports are working fine. They work grand with mice, keyboards, wireless USB dongle but when I go to plug in my memory stick or my external hard drive they wont work. Strange thing is when i first installed it (about 2 weeks ago) i did use my memory stick without any problem. However it has always had a problem with my external hard drive. At first it would see my external hard drive but not work with it. Now it doesn't see it or my memory stick (with which it used to work). 

The computer is a Dell Dimension 4400. It has 1.1 USB ports although I have installed a USB 2.0 PCI card so I have 4 USB 2.0 ports. I have also installed a new hard drive (160GB) and upgraded the RAM to 1 GB. Its well able to handle Ubuntu but I don't know why it is now completely not seeing my storage devices. Anyone know what could be wrong? If you need any more details ask. Thanks

---

### Post by rockyrobin on 2009-01-15
I too am having a similar problem......

I have 2 USB thumb drives - one is an old Crucial 64MB, and the other is a newer Corsair Flash Voyager 16GB.
Only the Crucial one will automount. The Corsair one is seen by the system but will not mount, although it works just fine with various other windows computers including the one with Ubuntu 8.10 installed in Windows XP (dual boot).

When I pop the Crucial one in a USB port I get the following from sudo tail -f /var/log/messages:-

Jan 15 13:00:18 chris-laptop kernel: [ 4150.768176] usb 1-2: new high speed USB device using ehci_hcd and address 8
Jan 15 13:00:18 chris-laptop kernel: [ 4150.947053] usb 1-2: configuration #1 chosen from 1 choice
Jan 15 13:00:18 chris-laptop kernel: [ 4150.981454] scsi4 : SCSI emulation for USB Mass Storage devices
Jan 15 13:00:23 chris-laptop kernel: [ 4155.986802] scsi 4:0:0:0: Direct-Access     Crucial  Gizmo            1.13 PQ: 0 ANSI: 0 CCS
Jan 15 13:00:23 chris-laptop kernel: [ 4156.005186] sd 4:0:0:0: [sdb] 125952 512-byte hardware sectors (64 MB)
Jan 15 13:00:23 chris-laptop kernel: [ 4156.006430] sd 4:0:0:0: [sdb] Write Protect is off
Jan 15 13:00:23 chris-laptop kernel: [ 4156.010055] sd 4:0:0:0: [sdb] 125952 512-byte hardware sectors (64 MB)
Jan 15 13:00:23 chris-laptop kernel: [ 4156.013057] sd 4:0:0:0: [sdb] Write Protect is off
Jan 15 13:00:23 chris-laptop kernel: [ 4156.020340]  sdb: sdb1
Jan 15 13:00:23 chris-laptop kernel: [ 4156.024077] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 15 13:00:23 chris-laptop kernel: [ 4156.027629] sd 4:0:0:0: Attached scsi generic sg2 type 0

Upon disconnecting the Crucial thumb drive I get the following:-

Jan 15 13:09:45 chris-laptop kernel: [ 4717.984256] usb 1-2: USB disconnect, address 10
Jan 15 13:09:45 chris-laptop kernel: [ 4717.990527] lost page write due to I/O error on sdb1


When I plug in the non working Corsair thumb drive I get the following:-

Jan 15 13:02:57 chris-laptop kernel: [ 4310.648201] usb 1-2: new high speed USB device using ehci_hcd and address 9
Jan 15 13:02:58 chris-laptop kernel: [ 4310.835752] usb 1-2: configuration #1 chosen from 1 choice
Jan 15 13:02:58 chris-laptop kernel: [ 4310.855483] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 15 13:03:08 chris-laptop kernel: [ 4321.480200] usb 1-2: reset high speed USB device using ehci_hcd and address 9

Upon disconnecting the Corsair thumb drive I get the following:-

Jan 15 13:04:29 chris-laptop kernel: [ 4402.494542] usb 1-2: USB disconnect, address 9
Jan 15 13:04:29 chris-laptop kernel: [ 4402.502150] scsi 5:0:0:0: Device offlined - not ready after error recovery


My Ubuntu 8.10 is a fresh install with only the Multimedia mods off the sticky thread elsewhere on this forum.

My laptop is a Fujitsu P7010 which is a typical first gen' Centrino with integrated graphics etc.

If any more info would be helpful in giving a clue to what is going on would be keen to help try and solve this problem.

Thanks for any help,

RR

---

### Post by dionp2 on 2009-01-17
I am also having the same problem.

I have a Toshiba A50 Notebook and cannot mount external hard drives or usb thumb drives.

I can through the command line but this is a pain and when I am in a business meeting the last thing I want to do is say excuse me I have to open a terminal to mount a bloody thumb drive. Which should be standard.

I installed pmount and rebooted but that also made no difference.

This is driving me bananas..

Any help would be kindly appreciated. 

Thankyou

D

---

### Post by dionp2 on 2009-01-17
Sorry I should have been clearer in my explination as to what is happening.

It brings the drive up on the KDE desktop but when trying to mount it (ie open in dolphin) it says "permission denied"

---

### Post by rockyrobin on 2009-01-18
As a followup i've managed to fix my problem so am popping the fix here incase it helps anyone else:-

The fix was to add:

echo 30 > /sys/module/scsi_mod/parameters/inq_timeout

in an rc startup script. (I placed mine in /etc/rc2.d/S99usb_inq_timeout.)

Some suggestions on the web included:

or in /etc/modprobe.conf

options usb_storage delay_use=20

That didn't work for me. Others also stated that the /etc/modprobe.conf fix didn't work for them either.

The site that got me going stated:

The default linux timeout is set for 5 secs, and the stick takes 14.5 seconds. So if you set the timeout to 15 seconds or more, and reinsert the stick, the stick should be mountable and readable. Just remember to add this to your boot scripts, or repeat it every time you reboot the kernel.

The inquiry timeout can be set to 15 sec with the following command line:
Code:

echo 15 >/sys/module/scsi_mod/parameters/inq_timeout

Or if you prefer the grub command line is :
Code:

scsi_mod.inq_timeout=15

I hope this longer timeout will someday be standard for the kernel.



This was ripped from another thread I found on the internet.

Hope it may be of help.

RR

---

### Post by Kanga on 2009-01-18
Hi rockyrobin,
I've tried typing " echo 15 >/sys/module/scsi/mod/parameters/inq_timeout "
in the terminal, and the message I got was " permission denied ".
I've also tried : system - administration - authorizations - storage - mount filesystem from removable drives, which supposedly gave me permission to mount the drives, rebooted and nothing's changed. Still wont recognise my usb memory stick until I type lsusb in the terminal. It then shows up in Places.

---

