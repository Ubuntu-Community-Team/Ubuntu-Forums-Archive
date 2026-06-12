---
title: "Dvd - Ram"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by cimphany on 2007-09-21
I cannot access my DVD RAM discs, All other discs work fine but DVD RAM gives me a problem.

The error I get is: 
-Cannot mount volume. Invalid mount option when attempting to mount the volume 'DVD_CAMERA'.

My Drive info is as follows:
-Vender: TSSTcorp
-Model: CD/DVDW SE-T084L
-Firmware 0000
-Connection: USB 2.0 at 480 Mbps
-Media: CD-RW/DVD+/-RW Drive
-Removable: Yes (ejectable)
-External: Yes

Volume Information:
Label: DVD_Camera
Size: 1.3GB
Media: DVD-RAM Disc
UUID: 
File System: udf


The port I'm connected to is USB 2.0
The drive runs fine under window's XP Media Center/Pro 

the drive is presented under the Samsung:
[http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=opticaldiscdrives&subtype=dvdwriter&model_cd=SE-T084L/EUBN](http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=opticaldiscdrives&subtype=dvdwriter&model_cd=SE-T084L/EUBN)

uname -a:  Linux agatha 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

About Ubuntu: Ubuntu 7.04  the Feisty Fawn - released in April 2007.

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=e637532b-c109-41a8-920a-ef7949eb6fed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=165C04125C03EAF7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=7E44AA3744A9F257 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=67632439-3a90-44e4-b7b4-7053c3883fcf none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

