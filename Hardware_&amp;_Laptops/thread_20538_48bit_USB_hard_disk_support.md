---
title: "48bit USB hard disk support"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by Michele Moglia on 2005-03-17
I hava Matrox 160 GB hard disk connected by USB to my laptop with Ubuntu.
I can use without any problem the lower 137 GB of the disk that is seen ad /dev/sda from my system but any software (parted, fdisk, qtpated) make me able to partition and use the upper 23 GB of the disk.
Every message and link I found about this problem speak about IDE/ATAPI but in my case the problem is by USB access.
There a solution in Hoary for this ? 
What have I to do to see the the end of my disk ?
Thanks everyone for help.
 :-$ 
Ciao

Michele

---

### Post by alastair on 2005-03-17
Take a look in the system log file for messages related to IDE/ATA (and USB). I know the host interface is USB, but the disk inside is IDE ofcourse.

Look through :

/var/log/syslog

or the output of "dmesg". Look for when the disk is probed - to see what the kernel thinks it has and any messages it prints (to see if there is a BIOS issue or not).

---

### Post by paul cooke on 2005-03-17
don't know... my Maxtor 160GB USB hard disk just plugged in and went... all 163GB of it is seen.

---

### Post by Michele Moglia on 2005-03-17
This the part of var/log/syslog about the hard disk.

Feb 19 17:06:33 ubuntu kernel: Initializing USB Mass Storage driver...
Feb 19 17:06:33 ubuntu kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Feb 19 17:06:39 ubuntu kernel:   Vendor: Maxtor 6  Model: Y160P0            Rev: YAR4
Feb 19 17:06:39 ubuntu kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Feb 19 17:06:39 ubuntu kernel: USB Mass Storage device found at 3
Feb 19 17:06:39 ubuntu kernel: usbcore: registered new driver usb-storage
Feb 19 17:06:39 ubuntu kernel: USB Mass Storage support registered.
Feb 19 17:06:39 ubuntu usb.agent[6545]:      usb-storage: loaded successfully
Feb 19 17:06:39 ubuntu scsi.agent[6606]: disk at /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:2.0/host0/0:0:0:0
Feb 19 17:06:39 ubuntu kernel: SCSI device sda: 268435455 512-byte hdwr sectors (137439 MB)
Feb 19 17:06:39 ubuntu kernel: sda: assuming drive cache: write through
Feb 19 17:06:39 ubuntu kernel:  /dev/scsi/host0/bus0/target0/lun0: p1 p2
Feb 19 17:06:39 ubuntu kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Feb 19 17:06:39 ubuntu udev[6647]: creating device node '/dev/sda1'
Feb 19 17:06:39 ubuntu udev[6648]: creating device node '/dev/sda2'
Feb 19 17:06:39 ubuntu udev[6645]: creating device node '/dev/sda'

I cannot see anything wrong, but I am not so expert about Linux.
There is one thing that I can tell more: the fact that the disk was formatted under
Windows 2000 and that it has two partition one NTFS and one EXT3.

Someone see something usefull in the log ?

Thanks

Michele

---

### Post by alastair on 2005-03-17
Could this be a BIOS issue? Perhaps :

- look through the BIOS and options for "USB legacy" or "PnP OS" -> disable
- upgrade the BIOS?

---

### Post by Sivel on 2005-03-17
I would say that this is a bios problem.  A lot of bioses have a 137GB limit.  Look into finding a bios upgrade.  Either that or try to disable Legacy USB support in the BIOS.  Then the bios generally wont look at USB devices during boot, so the bios doesn't really know anything about the drive and the OS can deal with it.

---

### Post by Michele Moglia on 2005-03-22
I have not any setting about USB in the BIOS
(The BIOS is Phoenx BIOS for Acer and exposes very few settings to the user).
And BIOS is the last available from Acer's site for my model of laptop.
Have you any other suggestion ?

Thanks

Michele

---

