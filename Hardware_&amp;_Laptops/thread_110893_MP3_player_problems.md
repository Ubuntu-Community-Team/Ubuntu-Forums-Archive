---
title: "MP3 player problems"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by lapark on 2005-12-31
Hi forumers,

I recently purchased a sansui mp3 player. Files are transferred using the computers USB port. At the moment it is detected, but I cannot mount it using linux. Using Windows XP, the drive mounts as FAT and file can be transferred.

When the drive is plugged in while using GNOME, a USB drive icon appears labelled SANSUI DIGITAL PLAYER. When I try to open the drive, a dialog box appears saying "Unable to mount the selected volume - Error: given UDI is not a mountable volume"

Using dmesg the following is found:
------
USB Mass storage support registered.
 Vendor: SANSUI     Model: DIGITAL PLAYER  Rev: 1.00
 Type:    Direct-Access                               ANSI SCSI revision: 00
SCSI device sda: 1036033 512-byte hdwr sectors (530 MB)
sda: test WP failed, assume write enabled
sda: assuming drive cache: write through
SCSI device sda: 1036033 512-byte hdwr sectors (530 MB)
sda: test WP failed, assume write enabled
sda: assuming drive cache: write through
  /dev/scsi/host0/bus0/target0/lun0:<6>SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 0
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 1
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 2
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 3
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 4
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 5
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 6
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 7
 unable to read partition table
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
usb-storage: device scan complete
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 0
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 1
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 2
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 3
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 4
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 5
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 6
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 7
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 8
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 9
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 10
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 11
printk: 27 messages suppressed
Buffer I/O error on device sda, logical block 11
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 12
.. repeat for sectors 13 to 61 ...
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 62
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 63
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 0
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 1
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 2
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 3
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 4
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 5
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 6
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 7
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 512
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 513
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 514
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 515
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 516
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 517
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 518
SCSI error : <0 0 0 0> return code = 0x1007000
end request: I/O error, dev sda sector 519
------

The device /dev/sda is created, but there is no /dev/sda1
Attempting to mount /dev/sda gives:
sudo mount -t vfat /dev/sda /mnt/sda1/
mount: /dev/sda: can't read superblock

Listing the partitions shows nothing:
sudo fdisk -l /dev/sda

I have been searching the Web for an answer, but have had no success. Some suggestions were:
* remove the module ehci_hcd, but it was not loaded
* recompile the kernel with CONFIG_EFI_PARTITION unset, but this was tried and failed.

Please help.
Thanks.

---

### Post by PolarBear64 on 2006-01-01
lapark I dont know if it will help but I had all kinds a trouble yesterday mounting my second drive and its partitions finally got it.

you might try
      making a new folder in media
               sudo mkdir /media/mp3player
then        sudo chmod -R 777 /media/mp3player

then        sudo mount -t vfat /dev/sda /media/mp3player

dont know if you need the vfat part i set mine all to automount but they are not removable.

here is the link to my thread also   [http://ubuntuforums.org/showthread.php?t=110763](http://ubuntuforums.org/showthread.php?t=110763)

hope ya get it working

---

### Post by lapark on 2006-01-02
Thanks for the reply, unfortunately it does not work. Here are the responses:

> sudo mount -t vfat /dev/sda /media/mp3player
[4295361.331000] FAT: unable to read boot sector
mount: /dev/sda: can't read superblock

> sudo mount -t auto /dev/sda /media/mp3player
[4295454.900000] Buffer I/O error on device sda, logical block 1035904
[4295454.918000] Buffer I/O error on device sda, logical block 1035905
[4295454.936000] Buffer I/O error on device sda, logical block 1035906
[4295454.952000] Buffer I/O error on device sda, logical block 1035907
[4295454.967000] Buffer I/O error on device sda, logical block 1035908
[4295454.982000] Buffer I/O error on device sda, logical block 1035909
[4295454.996000] Buffer I/O error on device sda, logical block 1035910
[4295455.009000] Buffer I/O error on device sda, logical block 1035911
[4295455.060000] Buffer I/O error on device sda, logical block 1035904
[4295455.077000] Buffer I/O error on device sda, logical block 1035905
[4295459.903000] Buffer I/O error on device sda, logical block 125
mount: you must specify the filesystem type

> sudo mount /dev/sda /media/mp3player
produces similar results to specifying -t auto

I know that the filesystem is FAT because I have successfully mounted it using WindowsXP. The block errors are all on high numbered blocks. Could it be that blocks past the last block are trying to be accessed?

Any suggestions would be appreciated.

---

### Post by lapark on 2006-01-04
Here is an update on the problem (which I think I understand now). After changing to the 2.6.7 kernel, the mp3 player produces no errors on insertion. I created the sda device (in /dev/sda using MAKEDEV) and successfully mounted it using:
> sudo mount -t vfat /dev/sda /media/mp3player

The same symptoms appear in this problem:
[http://kerneltrap.org/node/3650?PHPSESSID=b0f6a4f0d422df59aa76a1258b46750d](http://kerneltrap.org/node/3650?PHPSESSID=b0f6a4f0d422df59aa76a1258b46750d)

It seems that all I have to do to mount my mp3 player in kernel 2.6.12 is to add to the unusual_devs.h file and recomplie the kernel.

Has anyone had any experience in adding to unusual_devs.h?

---

### Post by lapark on 2006-01-05
Problem fixed

The mp3 player I was using produced information that the kernel thought was an error (hence all of the error messages in dmesg). To tell the kernel that this is alright, an entry must be placed in the drivers/usb/storage/unusual_devs.h kernel header file and the kernel recompiled.

The entry is of the form:

UNUSUAL_DEV(  0xVendor, 0xProdID, 0x0100, 0x0100, 
		Manufacturer,
		Product, 
		US_SC_DEVICE, US_PR_DEVICE, NULL,
		US_FL_IGNORE_RESIDUE ),

where Vendor, ProdID, Manufacturer and Product are replaced with the usb device values found in /proc/bus/usb/devices

I can now successfully mount my mp3 player (but unfortunately my wireless card has stopped talking, time to recompile the kernel again!)

Case closed.

---

