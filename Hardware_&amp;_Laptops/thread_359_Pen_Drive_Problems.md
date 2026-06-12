---
title: "Pen Drive Problems"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by FX on 2004-10-12
I'm still kind of new to Linux but my understanding is that hal is suppose to mount attachments automatically when they are hooked up to your pc. Like ipods and the likes. 

Well I have been trying to get my pen drive to work and Nautilus will not start up. Here is the output of my dmesg after I put the pen drive into the usb port. Anyone have any ideas?


Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor: Kingston  Model: DataTraveler 2.0  Rev: 4.10
  Type:   Direct-Access                      ANSI SCSI revision: 02
USB Mass Storage device found at 3
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
SCSI device sda: 503808 512-byte hdwr sectors (258 MB)
sda: Write Protect is off
sda: Mode Sense: 0b 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: [CUMANA/ADFS] p1&lt;5&gt;Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Buffer I/O error on device sda1, logical block 508378384
Buffer I/O error on device sda1, logical block 508378385
Buffer I/O error on device sda1, logical block 508378386
Buffer I/O error on device sda1, logical block 508378387
Buffer I/O error on device sda1, logical block 508378388
Buffer I/O error on device sda1, logical block 508378389
Buffer I/O error on device sda1, logical block 508378390
Buffer I/O error on device sda1, logical block 508378391
Buffer I/O error on device sda1, logical block 508378392
Buffer I/O error on device sda1, logical block 508378393
Buffer I/O error on device sda1, logical block 508378394
Buffer I/O error on device sda1, logical block 508378395
Buffer I/O error on device sda1, logical block 508378396
Buffer I/O error on device sda1, logical block 508378397
Buffer I/O error on device sda1, logical block 508378398
Buffer I/O error on device sda1, logical block 508378399
Buffer I/O error on device sda1, logical block 508378384
FAT: invalid media value (0xb9)
VFS: Can't find a valid FAT filesystem on dev sda1.
UDF-fs: No VRS found
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sda1.
VFS: Can't find ext3 filesystem on dev sda1.
VFS: Can't find ext2 filesystem on dev sda1.
ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1

Like I said I'm still kind of new at this so be gentle.  :D

FX

---

### Post by FX on 2004-10-13
Bump...... Anyone have an answer?   8) 

FX

---

### Post by randy on 2004-10-14
Try mounting the pen drive manually.  To do that you use the mount command and specify the drive and the mount pount.  

*mount /dev/sda1 MOUNTPOINT*

You may also have to specify the filesystem that is on the pen drive.

---

### Post by Flawed on 2004-10-14
Did you try reformatting the pen drive? I had a similar problem with my pen drive and Fedora and reformatting the drive (with a FAT filesystem) fixed the problem.

---

### Post by strandlooper on 2004-11-07
I experience similar mount problem with my Kingston Data Traveler 512MB.
The device is correctly recogniced by the drive manager but not mountabel by command line or others.

No mount problem on SuSE9.1 and xp. 

On Linuxquestion.org a post says that Debian can not mount Kingston 512MB but to format  the stick would fix the problem, but it didn't fixe my problem.

[http://www.linuxquestions.org/questions/showthread.php?s=&forumid=4&threadid=246273](http://www.linuxquestions.org/questions/showthread.php?s=&forumid=4&threadid=246273)

Any suggestion or advices

---

### Post by az on 2004-11-07
Some of these drives have an embedded hub or something that necessitates you using /dev/sda as opposed to /dev/sda1

Ubuntu or hotplug should pick up on that, though.

I tried to format /dev/sda1 on such a drive and ended up with a headache untill I fixed it...

---

### Post by jwenting on 2004-11-08
I've had the "bad superblock" message with one no-brand pendrive. 2 others (branded names) work just fine.

It's like with everything under Linux, hardware support is (still) somewhat hit and miss.
While in theory they're all the same in practice there are small differences that mean some work just fine and some don't work at all.

---

### Post by wernst on 2005-02-11
I had a Kingston Data Traveler pen drive that worked fine in Win98, XP, and OSX, but  Ubuntu Warty would complain about "Invalid Media Values" and "Buffer I/O Errors" at the console when it was inserted, and it refused to Mount.

I read this:
[http://lists.debian.org/debian-user/2004/12/msg04382.html](http://lists.debian.org/debian-user/2004/12/msg04382.html)

and figured that the parititon table was messed up on it. QTParted could repartition this pen drive, and then it would mount on the desktop ONE time only. None of my Windows utilities would repartition a USB pen drive, but my Mac's OS X Disk Utilities was happy to.

So I used to to blow away the partition table and create a new UNIX partition. Then I slapped it into Ubuntu and it mounted. I unmounted it and reformatted it with: 
#> mkfs -t vfat /dev/sda1

and it mounted fine. Then I slapped it back into windows and reformatted it FAT32.

Finally, I tried it again in Ubuntu, and it works fine now throughout all the platforms.

My Iomega keychain drives, on the other hand, worked just fine on all the OSes right out of the box.

I hope this helps...

-Warr

---

### Post by NRios on 2005-03-02
I don't think this has anything to do with fat vs vfat vs other filing systems or with the particular brand or model of flash bar.

I get exactly the same message when introducing a perfectly valid CDROM in the IDE drive. The drive spins up, then quiets down, and running dmesg throws that error.

---

### Post by NRios on 2005-03-02
Sorry for replying to myself, but I was blinded by my own problem and was not very exact.

The error I get with the CDROM is

   VFS: Can't find a HFS filesystem on dev hdc

no matter what CDROM I introduce. If I manually add

    /dev/hdc /mnt/cdrom auto user,noauto,ro 0 0 

to /etc/fstab, I can read the CD normally.

That's why I think it's got to do with gnome VFS, not with the various drives.

---

