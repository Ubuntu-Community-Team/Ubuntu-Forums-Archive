---
title: "hard disk queries"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by ylawayjdp on 2005-08-01
HI there I have been coping/ignoring my second hard drive in my pc since christmas.  I was too busy with uni work and part time job to get round to it.

However I have not been able to mount my 30gig slave drive under hoary

I get this output when I try sudo mount -a from shell:
wrong fs type, bad option, bad superblock on /dev/hdb1

then with dmesg | tail: 

attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
usb 3-1: USB disconnect, address 3
scsi1 (0:0): rejecting I/O to dead device
SCSI error: host 1 id 0 lun 0 return code = 4000000
        Sense class 0, sense error 0, extended sense 0
EXT3-fs: Unrecognized mount option "noaut" or missing value
EXT3-fs: Unrecognized mount option "noaut" or missing value

I found a similar query to mine by googling with an excellent answer [http://forum.pcmech.com/showthread.php?t=135737](http://forum.pcmech.com/showthread.php?t=135737) but the guy does not explain how to use the utility fdisk.  
I type sudo fdisk /dev/hdb1 then choose the option n to create a new partition.   Once I have done that I dont know whether to create an extended (e) partition or primary (p) there are also options 1-4 for each of these choices.

My aim is to create a disk space exclusively for media mp3, mpeg etc so I will not need to create a boot partition.  I run ubuntu exclusively so I do not need to be able to view the files in M$.  Any help with how I might need to mount/read/write the hard drive after might help.

Here is my fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdb1       /home/ylawayjdp/storage ext3    rw,user,noaut   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2       /media/ipod     fat3    rw,user,noauto  0       0

cheers
J

---

### Post by amohanty on 2005-08-01
> /dev/hdb1 /home/ylawayjdp/storage ext3 rw,user,noaut 0 0 

You are missing an _o_ in the noauto option.... :)

as indicated here:

> 
EXT3-fs: Unrecognized mount option "noaut" or missing value
EXT3-fs: Unrecognized mount option "noaut" or missing value
 

AM

---

### Post by ylawayjdp on 2005-08-01
My god can't believe I didn't spot it! Thats a Doh! moment if ever I had one!

Thanks for your help

J

---

