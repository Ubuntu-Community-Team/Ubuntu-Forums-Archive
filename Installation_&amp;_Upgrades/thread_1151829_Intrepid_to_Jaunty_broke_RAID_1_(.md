---
title: "Intrepid to Jaunty broke RAID 1 :("
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Robinmontreal on 2009-05-07
Hello all... I have been searching through the posts for help on my upgrade from Intrepid to Jaunty. I read a few posts regarding the mdadm.conf file being corrupted. But doing the mdadm --examine --scan config=mdadm.conf  thing did not do it for me, I also tried a few things on my own and still have not been able to boot into my raid,, i am sort of new to Ubuntu, Although i have been using Debian Etch for the last couple years..

I can boot up if i edit the grub at start up and make the boot disk /dev/sda1

Here is my current setup, any ideas would be helpful..

P.S i get kind of confused when it comes to UUIDs rather than devices...
Thanks to all in advance for your help!


/etc/mdadm/mdadm.conf

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sda[1-5] /dev/sdb[1-5]

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]rob@24365.ca[/email]

# This file was auto-generated on Mon, 06 Apr 2009 16:33:39 +0000
# by mkconf $Id$
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=9e55243e:7ff3a3bf:992a3195:d7fc34f7
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=b46972b4:86c82767:142fb8e7:1aa322f2
root@dewy:~# cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sda[1-5] /dev/sdb[1-5]

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]rob@24365.ca[/email]

# This file was auto-generated on Mon, 06 Apr 2009 16:33:39 +0000
# by mkconf $Id$
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=9e55243e:7ff3a3bf:992a3195:d7fc34f7
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=b46972b4:86c82767:142fb8e7:1aa322f2

/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=3ac09ddc-1b59-4d84-b171-f660a54f7c1b /               ext3    relatime,errors=remount-ro 0       1
# /dev/md1
#UUID=253d1000-36a2-4267-85df-2d766bceb346 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/md0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9e55243e:7ff3a3bf:992a3195:d7fc34f7 ro quiet splash bootdegraded=true 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic


cat /proc/mdstat

Personalities : [raid1] 
md0 : inactive sdb1[1](S)
      155252032 blocks
       
md1 : active raid1 sda5[0] sdb5[1]
      971776 blocks [2/2] [UU]
      
unused devices: <none>


blkid

root@dewy:~# blkid 
/dev/sda1: UUID="3e24559e-bfa3-f37f-9531-2a99f734fcd7" TYPE="mdraid" 
/dev/sda5: UUID="b47269b4-6727-c886-e7b8-2f14f222a31a" TYPE="mdraid" 
/dev/sdb1: UUID="3e24559e-bfa3-f37f-9531-2a99f734fcd7" TYPE="mdraid" 
/dev/sdb5: UUID="b47269b4-6727-c886-e7b8-2f14f222a31a" TYPE="mdraid" 
/dev/md1: TYPE="swap" UUID="253d1000-36a2-4267-85df-2d766bceb346"

---

### Post by Robinmontreal on 2009-05-07
SO i booted with a rescue cd as stated in a post i read, i tried to then mount /dev/md0 to /mnt/raid and when i try to open the menu.lst its all weird looking liek a binary... but if i boot from sdb1  or sda1 only all is fine.. does the file look weird because of the rescue cd?

I would hate to have to re-install everything from scratch, it would really suck...

Thanks..

---

### Post by aidan.dixon on 2009-05-08
Hi, Rob!

I have the same issue using Jaunty on amd64 hardware.  (2 500GB SATA discs, Intel Xeon X3220 CPU and Intel S3210SHLX motherboard.)

I have a two raid arrays made each from twp partitions (md1=sd[ab]7, md2=sd[ab]6).  (I probably should have made the array from two whole discs but only wanted the replication for two key partitions.)

After upgrading to Jaunty I find that the partitions on sdb cannot be added into the array as they are always "busy" although nothing appears to have them open (except see output of mdadm -q below).

Here's a bunch of relavent information for anyone who's interested.

root@scarlatti:~# mdadm -D /dev/md[12]
/dev/md1:
        Version : 00.90
  Creation Time : Sun Jan 25 21:58:19 2009
     Raid Level : raid1
     Array Size : 390732800 (372.63 GiB 400.11 GB)
  Used Dev Size : 390732800 (372.63 GiB 400.11 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri May  8 11:01:35 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5da99166:984a0dd0:4def2254:c08df2ca (local to host scarlatti)
         Events : 0.140

    Number   Major   Minor   RaidDevice State
       0       8        7        0      active sync   /dev/sda7
       1       0        0        1      removed
/dev/md2:
        Version : 00.90
  Creation Time : Fri Mar 13 23:04:49 2009
     Raid Level : raid1
     Array Size : 80075840 (76.37 GiB 82.00 GB)
  Used Dev Size : 80075840 (76.37 GiB 82.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri May  8 11:33:01 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9732d9bb:9dcb6632:4def2254:c08df2ca (local to host scarlatti)
         Events : 0.666

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        6        1      active sync   /dev/sda6
root@scarlatti:~# mdadm -q  /dev/sdb6
/dev/sdb6: is not an md array
/dev/sdb6: device 0 in 2 device mismatch raid1 /dev/md2.  Use mdadm --examine for more detail.
root@scarlatti:~# mdadm -q  /dev/sdb7
/dev/sdb7: is not an md array
/dev/sdb7: device 1 in 2 device mismatch raid1 /dev/md1.  Use mdadm --examine for more detail.
root@scarlatti:~# 
root@scarlatti:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3720

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1945    15623181   83  Linux
/dev/sda2            1946       60801   472760820   85  Linux extended
/dev/sda5            1946        2188     1951866   82  Linux swap / Solaris
/dev/sda6            2189       12157    80075961   83  Linux
/dev/sda7           12158       60801   390732898+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3720

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         609     4891761   83  Linux
/dev/sdb2             610        1945    10731420   83  Linux
/dev/sdb3            1946       60801   472760820   85  Linux extended
/dev/sdb5            1946        2188     1951866   82  Linux swap / Solaris
/dev/sdb6            2189       12157    80075961   83  Linux
/dev/sdb7           12158       60801   390732898+  83  Linux
root@scarlatti:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda6[1]
      80075840 blocks [2/1] [_U]
      
md1 : active raid1 sda7[0]
      390732800 blocks [2/1] [U_]
      
md_d2 : inactive sdb6[0](S)
      80075840 blocks
       
md_d1 : inactive sdb7[1](S)
      390732800 blocks
       
unused devices: <none>

---

### Post by aidan.dixon on 2009-05-08
Hi, Rob!

I have the same issue using Jaunty on amd64 hardware.  (2 500GB SATA discs, Intel Xeon X3220 CPU and Intel S3210SHLX motherboard.)

I have a two raid arrays made each from twp partitions (md1=sd[ab]7, md2=sd[ab]6).  (I probably should have made the array from two whole discs but only wanted the replication for two key partitions.)

After upgrading to Jaunty I find that the partitions on sdb cannot be added into the array as they are always "busy" although nothing appears to have them open (except see output of mdadm -q below).

Here's a bunch of relavent information for anyone who's interested.

root@scarlatti:~# mdadm -D /dev/md[12]
/dev/md1:
        Version : 00.90
  Creation Time : Sun Jan 25 21:58:19 2009
     Raid Level : raid1
     Array Size : 390732800 (372.63 GiB 400.11 GB)
  Used Dev Size : 390732800 (372.63 GiB 400.11 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri May  8 11:01:35 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5da99166:984a0dd0:4def2254:c08df2ca (local to host scarlatti)
         Events : 0.140

    Number   Major   Minor   RaidDevice State
       0       8        7        0      active sync   /dev/sda7
       1       0        0        1      removed
/dev/md2:
        Version : 00.90
  Creation Time : Fri Mar 13 23:04:49 2009
     Raid Level : raid1
     Array Size : 80075840 (76.37 GiB 82.00 GB)
  Used Dev Size : 80075840 (76.37 GiB 82.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri May  8 11:33:01 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9732d9bb:9dcb6632:4def2254:c08df2ca (local to host scarlatti)
         Events : 0.666

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        6        1      active sync   /dev/sda6
root@scarlatti:~# mdadm -q  /dev/sdb6
/dev/sdb6: is not an md array
/dev/sdb6: device 0 in 2 device mismatch raid1 /dev/md2.  Use mdadm --examine for more detail.
root@scarlatti:~# mdadm -q  /dev/sdb7
/dev/sdb7: is not an md array
/dev/sdb7: device 1 in 2 device mismatch raid1 /dev/md1.  Use mdadm --examine for more detail.
root@scarlatti:~# 
root@scarlatti:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3720

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1945    15623181   83  Linux
/dev/sda2            1946       60801   472760820   85  Linux extended
/dev/sda5            1946        2188     1951866   82  Linux swap / Solaris
/dev/sda6            2189       12157    80075961   83  Linux
/dev/sda7           12158       60801   390732898+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3720

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         609     4891761   83  Linux
/dev/sdb2             610        1945    10731420   83  Linux
/dev/sdb3            1946       60801   472760820   85  Linux extended
/dev/sdb5            1946        2188     1951866   82  Linux swap / Solaris
/dev/sdb6            2189       12157    80075961   83  Linux
/dev/sdb7           12158       60801   390732898+  83  Linux
root@scarlatti:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda6[1]
      80075840 blocks [2/1] [_U]
      
md1 : active raid1 sda7[0]
      390732800 blocks [2/1] [U_]
      
md_d2 : inactive sdb6[0](S)
      80075840 blocks
       
md_d1 : inactive sdb7[1](S)
      390732800 blocks
       
unused devices: <none>

---

### Post by aidan.dixon on 2009-05-08
Hmmmm.... blkid output is interesting

root@scarlatti:~# blkid
/dev/sda1: UUID="6c026a4b-cd43-4069-8e5f-4b596b297963" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="85dfafe7-bef5-45fe-b4ad-704947b94ad5" 
/dev/sda6: LABEL="/export/home0" UUID="5c8cf208-07e1-42eb-8842-2dfcd8140213" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda7: LABEL="/export/home1" UUID="5dd16483-e282-468f-950d-1ef7043e2e64" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="70b03f51-cc99-4312-8a08-bdd7393e4963" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="85fde348-2e62-48f0-9f74-5b580ff4f785" 
/dev/sdb6: UUID="5c8cf208-07e1-42eb-8842-2dfcd8140213" SEC_TYPE="ext2" TYPE="ext3" LABEL="/export/home0" 
/dev/sdb7: UUID="6691a95d-d00d-4a98-5422-ef4dcaf28dc0" TYPE="mdraid" 
/dev/md1: LABEL="/export/home1" UUID="5dd16483-e282-468f-950d-1ef7043e2e64" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md2: LABEL="/export/home0" UUID="5c8cf208-07e1-42eb-8842-2dfcd8140213" SEC_TYPE="ext2" TYPE="ext3" 
root@scarlatti:~# 

Not sure how this happens.  I suspect I am going to need to back up my data and recreate my arrays from scratch.

MDadm.conf is basic (even unmodified, I think):

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sat, 24 Jan 2009 22:47:16 +0000
# by mkconf $Id$

---

### Post by aidan.dixon on 2009-06-19
Just for anyone interested, the kernel log showed that the 2nd device in each raid1 array (those on /dev/sdb) was being kicked off the array for not being fresh.

for some reason, doing mdadm --assemble -s was adding these two devices to /dev/md_d1 and /dev/md_d2 so I couldn't add them back to my original arrays /dev/md1 and /dev/md2.  This was fixed by doing 

# mdadm -S /dev/md_d1
# mdadm -S /dev/md_d2
# mdadm /dev/md2 -add /dev/sdb6
# mdadm /dev/md1 -add /dev/sdb7

This fixed the issue and allowed the raid1 arrays to be rebuilt and the out-of-sync drivers resynchronised.

There was still an issue with Jaunty not recognising the arrays at power up.  The only way I could fix this was to add array definitions to /etc/mdadm.conf

# definitions of existing MD arrays
ARRAY /dev/md1 uuid=5da99166:984a0dd0:4def2254:c08df2ca
ARRAY /dev/md2 uuid=9732d9bb:9dcb6632:4def2254:c08df2ca

---

### Post by yekim on 2009-06-24
Hey guys, I think I am having a similar problem, but following this thread I was unable to resolve it (I'm somewhat of a nub when it comes to this).

I have two 160GB disks (GParted shows them as /dev/sdb and /dev/sdc).  I had these setup using mdraid RAID1 (backup for family photos, etc.) using the tutorial I found here: [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid) 

I ran an update to Jaunty and ever since my raid drive is no longer mounting.  Here is some data that I hope helps:

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bc79f425-307f-4416-8d1d-6c350695f871 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b94961f7-a0fb-46fd-bb5a-70e5551ae977 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0        /home/mike/Data           ext3      defaults,relatime      0       0
```

mike@Yekbu:~$ blkid
```

/dev/sda5: TYPE="swap" UUID="b94961f7-a0fb-46fd-bb5a-70e5551ae977" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: LABEL="SERVICEV001" UUID="50C1-D9F0" TYPE="vfat" 
/dev/sdc: UUID="4eb71553-941a-2c69-93be-8052222a643f" TYPE="mdraid" 
/dev/sda1: UUID="bc79f425-307f-4416-8d1d-6c350695f871" TYPE="ext3" 
/dev/sdb: UUID="4eb71553-941a-2c69-93be-8052222a643f" TYPE="mdraid" 

```

mike@Yekbu:~$ cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb[0](S)
      156290816 blocks
       
unused devices: <none>

```

mike@Yekbu:~$ mdadm --assemble -s
```

mdadm: No arrays found in config file or automatically

```

Also I've noticed that /etc/mdadm.conf is blank / does not exist.

Thanks very much for your help!!
Yek

---

