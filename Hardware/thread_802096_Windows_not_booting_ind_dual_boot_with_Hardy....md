---
title: "Windows not booting ind dual boot with Hardy..."
date: 2008-05-21
forum: Hardware
---

### Post by ashwinidhiman on 2008-05-21
I have  a laptop with dual-boot enabled (Windows XP and Ubuntu Gutsy). I performed a network upgrade (to Hardy Heron) which seemed to give me some problems. So i performed a clean install and did only installed the / partition over the previous one and only mounted the other partitions.
Since then I could not boot into my Windows XP drive. Every time I try to boot into it I get the error 

Error 12:Invalid Device Requested
Press any key to continue...

I tried many other combinations like (hd0,0) to (hd0,9) but got one or the other of the following errors

Error 12:Invalid Device Requested
Press any key to continue...
OR
Error 22:No such partition
Press any key to continue...

The menu.lst contents pertaining to the Windows partition are

title		Windows XP
root		(hd0,5)
makeactive
chainloader	+1

The contents of /etc/fstab are

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=222f0e0e-874a-4855-860c-14502b2e5845 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1322-BF10  /extra          vfat    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=eaf072ac-3b53-4f98-acbc-8b4924ad84bd /home           ext3    relatime        0       2
# /dev/sda7
UUID=45CF-A040  /myall          vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=76C8EEADC8EE6AB7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=4334f667-a9be-47e8-9a10-c28a7cd731eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

The output of sfdisk -d /dev/sda is 

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    16065, size=156280320, Id= f, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=    16128, size= 20482812, Id= 7
/dev/sda6 : start= 46668888, size=  2040192, Id=82
/dev/sda7 : start= 48709143, size= 92245167, Id= b
/dev/sda8 : start= 34170318, size= 12498507, Id= b
/dev/sda9 : start=140954373, size= 13253562, Id=83
/dev/sda10: start=154207998, size=  2088387, Id= b
/dev/sda11: start= 20499003, size= 13671252, Id=83

Now I want to boot into my Windows drive otherwise I would have to start all over again and install Windows again and install Ubuntu over it again.
Please help me out of it...

---

