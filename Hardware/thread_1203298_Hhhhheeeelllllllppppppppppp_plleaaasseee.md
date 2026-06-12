---
title: "Hhhhheeeelllllllppppppppppp plleaaasseee"
date: 2009-07-03
forum: Hardware
---

### Post by npm1 on 2009-07-03
my hard drive is playing up in some weird way
when i plug the hard drive in to the computer it comes up on my ubuntu 9.04 desktop and loads as expected with no errors----
when i o-pen the hard drive up all folders are their in fact on the bottom bit it says 106 items, Free space 170.2gb

how ever when i go into one of the folders it says   0 items, Free Space: 170.2gb

etc/fstab file looks as follows:

[I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a3e95b8a-9daa-45bd-b056-399c8f0113a6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca1126e6-a476-4ac1-b0c5-620091587f3d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
###########new to linux
UUID=7929-f69c /media/Elements vfat utf8,umask=007,gid=1000[/I]

i made changes to it as soon as found this out
removing the "new to linux" bit

my new fstab is minus that bit------------------------,.........    


i even pluged into into windows and same incident was present

---

### Post by npm1 on 2009-07-03
PLEASE HELP ITS DYA 


I DO NOT WANT TO LOOSE THE DATA 
OR END UP HAVING TO REFORMATT IT 
THE EXTERNAL HARD DRIVE IS AS FOLLOWS:

WESTERN DIGITAL 650GB FAT32

WHEN I TYPE SUDO FDISK -L INTO UBUNTU TERMINAL

THE FOLLOWING COMES UP:

/dev/sda1   *           1        9544    76662148+  83  Linux
/dev/sda2            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)

 AND THEN I TYPE  SUDO BLKID
THE FOLLOWING COMES UP--

/dev/sda1: UUID="a3e95b8a-9daa-45bd-b056-399c8f0113a6" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ca1126e6-a476-4ac1-b0c5-620091587f3d" 
/dev/sdb1: LABEL="Elements" UUID="7929-F69C" TYPE="vfat"

---

### Post by npm1 on 2009-07-03
ONE OF MY PREVIOUS POST WAS TO GAIN FULL PERMISSIONS OVER THE DRIVE THE PERSON WHO HELP GAVE ME THE FOLLOWING GUIDANCE WHICH IN TURN I FOLLOWED:
---------------------------------------------------------------------------------------------------------------------------------

**Re: Hard drive permissions----------------** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				sorry but it comes up as this:

on my terminal
@:~$ sudo fstab -l
[sudo] password for m:
sudo: fstab: command not found 			 		 	 	 
I'm sorry, but i gave you the wrong command name. Instead of sudo fstab -l you have to do [COLOR=Red]sudo fdisk -l[/COLOR].

 	Quote:
 	 	 		 			 				what is the umask === number usually 			 		 	 	 
umask=007 means, that you (and only you) get read,write and excute permissions for the partition.

 	Quote:
 	 	 		 			 				but where does the
/media/sda6_fat32 come from-is that simply the location of that drive 			 		 	 	 
This is the location, where my partition is mounted, i forgot to tell you, that you first have to create a directory with that name so before mounting it you should do [COLOR=Red]sudo mkdir /media/name_of_your_partition[/COLOR] (you can choose any name you like, e.g. on my system i named it /media/sda6_fat32)

 	Quote:
 	 	 		 			 				and finally utf8 			 		 	 	 
this is the codepage-style, on modern systems it's best to use utf8.

Here, in short the steps again:
1. sudo fdisk -l      ====> find out the name of your fat32 partition

2. blkid      ====> find out the UUID for your fat32 partition

3. sudo mkdir /media/your_partition_name

4. sudo gedit /etc/fstab and make the following entry at the end of the file:
 	Quote:
 	 	 		 			 				UUID=your_uuid /media/your_partition_name vfat utf8,umask=007,gid=46 0 1 			 		 	 	 
Take in mind that the entry in your /etc/fstab file must be exactly in that way, including spaces, commas etc.


--------------------------------------------------------------------------------------------------------------------------------



WHEN I TYPE THE FOLLOWING:
IT COMES UP AS----
:~$ sudo id 
uid=0(root) gid=0(root) groups=0(root),100(users),1000(nazim)

WHEN I TYPE THE FOLLOWING:
IT COMES UP AS----

~$ id
uid=1000(nazim) gid=1000(nazim) groups=0(root),4(adm),20(dialout),24(cdrom),46(plugdev),100(users),106(lpadmin),121(admin),122(sambashare),1000(nazim)

---

### Post by npm1 on 2009-07-03
please PLEASE HELP

---

### Post by bjdodo on 2009-07-03
Hi

"i even pluged into into windows and same incident was present"

If this is the situation then I doubt that playing with fstab or actually any configuration would help. I guess in this situation your file system is broken (probably the harddisk itself is faulty). I think in Windows you use scandisk to fix such problems, in Linux actually I'd try this software: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page). I do not know if they fix FAT problems, I used it to fix reiserFS problems.

Good luck!

Jozsi

---

### Post by npm1 on 2009-07-03
> **bjdodo said:**
> hi

"i even pluged into into windows and same incident was present"

if this is the situation then i doubt that playing with fstab or actually any configuration would help. I guess in this situation your file system is broken (probably the harddisk itself is faulty). I think in windows you use scandisk to fix such problems, in linux actually i'd try this software: [http://www.sysresccd.org/main_page](http://www.sysresccd.org/main_page). I do not know if they fix fat problems, i used it to fix reiserfs problems.

Good luck!

Jozsi

did it fix your external hard drive running such utility

---

### Post by bjdodo on 2009-07-03
Temporarily yes but my HD had bad sectors so I had to dump it. But I was able to use it for a while...

---

