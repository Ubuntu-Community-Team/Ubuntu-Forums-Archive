---
title: "USB floppy drive won't automount"
date: 2011-03-21
forum: Hardware
---

### Post by Snowhog on 2011-03-21
Ubuntu 10.04 32-bit fully up to date, running as a VM in Oracle VirtualBox 4.0.4 r70112.
Bus 001 Device 006: ID 0644:0000 TEAC Corp. Floppy

The device is seen during the boot process:
> [    6.765481] scsi 2:0:0:0: Direct-Access     TEAC     FD-05PUW         3000 PQ: 0 ANSI: 0 CCS
[    6.782807] sd 2:0:0:0: Attached scsi generic sg1 type 0

An icon (Floppy Drive) appears in Places > Computer. When a diskette is inserted (in this case, a VFAT formatted diskette with content) the disk drive reads the diskette and dmesg reports:
> [  388.243043] sd 2:0:0:0: [sda] 2880 512-byte logical blocks: (1.47 MB/1.40 MiB)
[  388.307300] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  388.499006] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  388.499176]  sda:


Double-clicking on the Floppy Drive icon does nothing. Ubuntu has not 'mounted' the diskette.

In Kubuntu (10.04, 10.10, and 11.04) which are installed on the same PC, the drive and inserted diskette are seen and mounted and can be accessed by the non-root user.

Why does Ubuntu not do the same? How do I get Ubuntu to properly see, mount, and make available to me (non-root user) floppy diskettes?

---

### Post by Snowhog on 2011-03-21
Solution found here in Ubuntuforums at [http://ubuntuforums.org/showthread.php?t=1641104](http://ubuntuforums.org/showthread.php?t=1641104)

With the USB Floppy drive connected, open a Terminal and type:
```
sudo blkid -c /dev/null
```
to find the drives /dev/xxx enumeration. Here, it's /dev/sda

In the Terminal type:
```
udisks --mount /dev/sda
```
(again, this is for my enumerated floppy drive)

The floppy mounts and is shown in Places. If the diskette has a label, it's identified with the label name. If it's an unlabeled diskette, it appears as **disk**

Click on it and it opens in Nautilis with your permissions.

---

### Post by Jared Norris on 2011-03-22
Thanks for doing all the legwork. I just had this exact same problem.:D

---

### Post by Curbuntu on 2011-03-25
Snowhog,

Thanks for this solution.  The problem has been driving me crazy for weeks, and this works.

I could use help with one more aspect of this, namely, writing an IMG file to the floppy, now that the drive can be read.  I can't find a GUI-based program that will tackle this project, and my attempts with dd have failed me so far.

FWIW: 

1) Your blkid command yields "sdc" as the answer sought;

2) The udisks command says that the FDD is called "/media/S3 DRV1".  (Yes, there's a space in "S3 DRV1".)

When I try something llke **dd if=/home/curbuntu/Downloads/SpinRite.img of=/media/S3 DRV1**, I get an error saying that /media/S3 DRV1 is a "is a directory."

---

### Post by slackerforlife on 2013-03-29
HI Curbuntu,

To fix your problem:

When I try something llke **dd if=/home/curbuntu/Downloads/SpinRite.img of=/media/S3 DRV1**, I get an error saying that /media/S3 DRV1 is a "is a directory."

You need to do it like this:
**dd if=/home/curbuntu/Downloads/SpinRite.img of=/media/S3 DRV1/****SpinRite.img**

you need to add the name of the file back to the end of your location.

And for the automount "plug and play" I found this to work on ubuntu 12.04

*Edit &#8220;/lib/udev/**rules.d/**80-udisks.**rules&#8221; and search for the lines*
* &#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8211;*
* # PC floppy drives*
* #*
* KERNEL==&#8221;fd*&#8221;, ENV{ID_**DRIVE_FLOPPY}**=&#8221;1&#8243;*
 *# USB floppy drives*
* #*
* SUBSYSTEMS==&#8221;usb&#8221;, ATTRS{bInterfac**eClass}**==&#8221;08&#8243;, ATTRS{bInterfac**eSubClass}**==&#8221;04&#8243;, ENV{ID_**DRIVE_FLOPPY}**=&#8221;1&#8243;*
* &#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8212;&#8212;-**&#8211;*
 *Replace those &#8220;1&#8243; (ones) with &#8220;0&#8243; (zeros). That&#8217;s all the magic.*
* Now restart the udev daemon by typing &#8220;invoke-rc.d udev restart&#8221;*

---

