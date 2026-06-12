---
title: "cd reads fine, dvd does not"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by pldobs on 2007-09-09
I have a dell Inspiron 5100 running ubuntu 7.04.  It has the stock DVD drive.  When I insert a CD, it auto mounts and works normally.  When I insert a DVD and try to browse, I get a message saying there is probably no media in the drive.  I know my drive is good because I have a dual boot system and when booting into windows, I am able to browse the DVD without a problem.

Any ideas?  Technical Info below.

Thanks!

Here is output from lshw
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SN-324F
                vendor: SAMSUNG
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: U203
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=c016fdd6-1e9e-49fb-b2d4-5467ff5ef968 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=4C5427384326FBD5 /media/hdc2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc3
UUID=45CE-5DE4  /media/hdc3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=586400c1-59eb-4f34-9270-159a34f6a325 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by x64Jimbo on 2007-09-09
Have you installed the necessary codecs?
Try Automatix to get that stuff working for you. Check the link in my sig.

---

### Post by pldobs on 2007-09-09
Thanks for the reply! The link to Automatix did not work.  The server must be down.  I may be missing the proper video CODECS.  Although, could a missing CODEC prevent the drive from recognizing that there is a disk in the disk drive?  I am not trying to play any movies. I am just trying to read files on DVD media.

---

### Post by x64Jimbo on 2007-09-09
Codecs may not be the right word. DVDs are protected with CSS encryption, and you need a driver for Linux called DeCSS that unscrambles the disc so it can even be read. Interesting that the Automatix site is down... 
EasyUbuntu is another program that works the same way - it installs all kinds of useful stuff that doesn't come with Ubuntu by default. 
[http://easyubuntu.freecontrib.org/overview.html](http://easyubuntu.freecontrib.org/overview.html)
The one you're looking for is called libdvdcss - you can see it in the picture on that page.

---

