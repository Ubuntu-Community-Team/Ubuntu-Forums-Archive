---
title: "Grub problems - Error 17 but not I think"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by novice buntu on 2009-10-06
Hi,

I (also) have grub pain. 

LSI Logic Ultra320 SCSI Adapter with 3 SCSI drives + 1 SATA drive

When I installed my Ubuntu 8.10, I forgot to attach a SCSI drive. I realized some time later. When I powered up the drive and tried to boot my PC I got error 17 from grub. 

I tried a number of things, most drastically, fdisking  all the partitions on my Ubuntu disk, reformating them and installing Ubuntu 9.4. However no matter what I try as long as the 3rd SCSI drive is attached I get error 17.

I booted with the install CD, saw and mounted all the drives individually. chroot, tried to use grub to setup (hd3,1) but I get one form of error or another depending on whether or not I have chroot'ed. If I chroot, the probe happens very quickly and *find* doesn't return anything. If I chroot, I get an error from setup(hd3) "Can't find /boot/stage1.." I checked the UUIDs in the menu.lst, all is correct

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

I have formatted and resized /boot as ext2 so I don't think error 17 is the problem.

I could use a few ideas as I'm all out. Any thoughts anyone?
TIA,

---

### Post by arrange on 2009-10-06
What are the systems on the other disks? Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"), or at least ```
sudo fdisk -l
sudo blkid -c /dev/null
```

Are you able to use UUID instead of (hdx,y)?

---

### Post by novice buntu on 2009-10-06
Thanx for taking the time.

Here's the fdisk. I have booted from install CD. All the other drives are NTFS (windoze). As I said I only get the error when /dev/sdc is powered-up.

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4cd1c09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 36.9 GB, 36969185280 bytes
255 heads, 63 sectors/track, 4494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4b3c8f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4493    36089991    7  HPFS/NTFS

Disk /dev/sdc: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9b50246

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8924    71681998+   7  HPFS/NTFS

Disk /dev/sdd: 36.9 GB, 36969185280 bytes
255 heads, 63 sectors/track, 4494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13338976

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          18      144553+  83  Linux
/dev/sdd2              19        1586    12594960   83  Linux
/dev/sdd3            1587        1652      530145   82  Linux swap / Solaris
/dev/sdd4            1653        4494    22828365    5  Extended
/dev/sdd5            1653        4494    22828333+  83  Linux

```

/dev/sdc has one NTFS partition. Is that marked as first boot?

I've uploaded the results.txt from the boot_info_script

I also tried
```
root@ubuntu:~/Desktop# mkdir /target
root@ubuntu:~/Desktop# mount -t ext4 /dev/sdd2 /target
root@ubuntu:~/Desktop# mount -t ext2 /dev/sdd1 /target/boot
root@ubuntu:~/Desktop# chroot /target /bin/bash
root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time...
grub> find /boot/grub/menu.lst

Error 15: File not found

grub> find /boot/grub/stage1  

Error 15: File not found

grub> find (hd ...tab
grub> find (hd3 ...tab
grub> find (hd3, ...tab
Error 21: Selected disk does not exist

grub> find (hd0 ...tab
grub> find (hd0, ...tab
Error 21: Selected disk does not exist

```

That probe was too quick. I think there is a issue using grub in this way. Are there any hints here?

Thanx.
Dp.

---

### Post by arrange on 2009-10-06
With all the drives attached, ALL options give you Error 17?```
Ubuntu 9.04, kernel 2.6.28-15-generic
Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Other operating systems:
Microsoft Windows XP Professional
```

---

### Post by novice buntu on 2009-10-06
I don't get a menu at all. The error kicks in just as BIOS hands over. Even if I boot from the CD and choose the boot from first disk option I get something like 


```

stage 1.5

Error 17

```

---

### Post by presence1960 on 2009-10-06
Go into BIOS please & report back the hard disk boot order.

---

### Post by arrange on 2009-10-07
What I would do is this:

1 setup BIOS so that it boots *sdd* first
2 run LiveCD and Terminal there
3 run **sudo grub** and install grub on sdd MBR (no chrooting necessary)
```
find /grub/stage2
root (hdx,y)
setup (hdx)
quit

```where x,y are numbers from the output of *find /grub/stage2* command.

Now the problematic part is to find the correct addressing for the Windows boot in *menu.lst*. The numbers in (hda,b) could be different with and without the extra drive attached and, as far as I know, you can't use UUID or LABEL for Win partitions. So you will probably have to experiment there.

You could also check the *Editing GRUB's device.map* section on [this page]("http://members.iinet.net/~herman546/p15.html").

BTW, are you going to attach the new drive permanently?

---

### Post by presence1960 on 2009-10-07
> **arrange said:**
> 

Now the problematic part is to find the correct addressing for the Windows boot in *menu.lst*. The numbers in (hda,b) could be different with and without the extra drive attached and, as far as I know, you can't use UUID or LABEL for Win partitions. So you will probably have to experiment there.


No experimenting necessary, that is why I asked for the order of hard disk booting in BIOS. When using (hdx,y) in GRUB x is determined by the order of hard disk boot in BIOS. 

Before I gave OP instructions on how to set up GRUB, I wanted that info also so I could explain how to edit menu.lst so windows will boot from the GRUB menu once GRUB is set up.

There is no reason to guess or experiment, GRUB is very orderly and detailed. All you need is the correct info to set it up properly.

---

### Post by novice buntu on 2009-10-07
I had a quick attempt at this morning. I have been a bit of a spanner I now realise. I didn't think to look at the BIOS. The BIOS can specify the disk boot order of the disks it can **see** on the SCSI controller. It's not an on-board controller so I was surprised by that. 

I experimented a bit. Set the wrong disk as the 1st boot and got an NT loader error. I have 2 HITACHI 36GB drives. One of them is Ubuntu, the other Windows. I had a look in /proc/scsi/scsi. The disks I am concerned with are ID:0 and ID:2. I set ID:2 as the 1st boot. Booted from the CD and followed the code from your last post (thanx). It appeared to work. At least I didn't get any errors from grub this time. However when I booted I got the same error. 

```

Loading Grub. Stage 1.5
Error 17

```

A couple of questions:

You said install grub on the MBR of /sdd. Does the code snippet you supplied do that or is there another step to get the MBR pointing to the correct root drive?

find /grub/stage2 returned (hd3,0)
Should I then set root as (h3,1) as my / (root partition) is on /dev/sdd2. Assuming grub is indexing the partitions from 0 (zero).


Yes I do want to keep this drive on-line permanently. It has a lot of data on.

I appreciate what your saying about the Windoze partition. I expect that will be easily fixed by editing the menu.lst and a bit of trial and error.

Thanx for you help so far. I don't think I'm that far away from getting this fixed.
Dp.

---

### Post by novice buntu on 2009-10-07
Sorry Presence, I think we cross-posted.

I have changed the boot order in the BIOS now so it may not be what it was. The current disk order is 

SCSI ID:2
SCSI ID:0
SATA disk
SCSI ID:8

I'm fairly certain that ID2 is the Ubuntu disk. As both disks are manufactured by Hitachi and are the same size it's tricky to determine which device is which. 

From the boot_info script it looks like I may have grub installed on both /sda and /sdb. 

If I change the boot order, do I also change the device naming scheme?

============================= Boot Info Summary: 

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd


I'm not by my machine at the moment. It will be a few hours before I'm home again and can work on it.

Thanx,
Dp.

---

### Post by presence1960 on 2009-10-07
> **novice buntu said:**
> Sorry Presence, I think we cross-posted.

I have changed the boot order in the BIOS now so it may not be what it was. The current disk order is 

SCSI ID:2
SCSI ID:0
SATA disk
SCSI ID:8

I'm fairly certain that ID2 is the Ubuntu disk. As both disks are manufactured by Hitachi and are the same size it's tricky to determine which device is which. 

From the boot_info script it looks like I may have grub installed on both /sda and /sdb. 

If I change the boot order, do I also change the device naming scheme?

============================= Boot Info Summary: 

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd


I'm not by my machine at the moment. It will be a few hours before I'm home again and can work on it.

Thanx,
Dp.

why don't you post the rest of the boot info script output. This will help sort out what you have especially since you posted your new boot order in BIOS.

---

### Post by novice buntu on 2009-10-07
It was attached in reply #3. Here it is again.

```

============================= Boot Info Summary: ======

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdd3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4cd1c09

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 36.9 GB, 36969185280 bytes
255 heads, 63 sectors/track, 4494 cylinders, total 72205440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4b3c8f8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    72,180,044    72,179,982   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders, total 143374738 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9b50246

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   143,364,059   143,363,997   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 36.9 GB, 36969185280 bytes
255 heads, 63 sectors/track, 4494 cylinders, total 72205440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13338976

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       289,169       289,107  83 Linux
/dev/sdd2             289,170    25,479,089    25,189,920  83 Linux
/dev/sdd3          25,479,090    26,539,379     1,060,290  82 Linux swap / Solaris
/dev/sdd4          26,539,380    72,196,109    45,656,730   5 Extended
/dev/sdd5          26,539,443    72,196,109    45,656,667  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F0A86F72A86F366E" LABEL="data" TYPE="ntfs" 
/dev/sdb1: UUID="88C04AEEC04AE254" TYPE="ntfs" 
/dev/sdc1: UUID="B62C2BB42C2B6F15" LABEL="scratch" TYPE="ntfs" 
/dev/sdd1: UUID="397b6599-eb59-470f-aea7-aacd3783fefe" TYPE="ext2" 
/dev/sdd2: UUID="c7ef1737-f93f-49ad-875b-e8ff86316e28" TYPE="ext4" 
/dev/sdd3: TYPE="swap" UUID="8c35836b-a13f-4e1d-a72a-d3cffdfa077f" 
/dev/sdd5: UUID="712d1f12-12ad-4199-94b1-af9ee7c649db" TYPE="ext4" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/scratch type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd2 on /media/disk-1 type ext4 (rw,nosuid,nodev,uhelper=hal)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer


============================= sdd1/grub/menu.lst: =============================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=397b6599-eb59-470f-aea7-aacd3783fefe

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		397b6599-eb59-470f-aea7-aacd3783fefe
kernel		/vmlinuz-2.6.28-15-generic root=UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		397b6599-eb59-470f-aea7-aacd3783fefe
kernel		/vmlinuz-2.6.28-15-generic root=UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 ro  single
initrd		/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		397b6599-eb59-470f-aea7-aacd3783fefe
kernel		/vmlinuz-2.6.28-11-generic root=UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		397b6599-eb59-470f-aea7-aacd3783fefe
kernel		/vmlinuz-2.6.28-11-generic root=UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		397b6599-eb59-470f-aea7-aacd3783fefe
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=================== sdd1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: initrd.img-2.6.28-15-generic
    .0GB: vmlinuz-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-15-generic

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd2 during installation
UUID=c7ef1737-f93f-49ad-875b-e8ff86316e28 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdd1 during installation
UUID=397b6599-eb59-470f-aea7-aacd3783fefe /boot           ext2    relatime        0       2
# /var was on /dev/sdd5 during installation
UUID=712d1f12-12ad-4199-94b1-af9ee7c649db /var            ext4    relatime        0       2
# swap was on /dev/sdd3 during installation
UUID=8c35836b-a13f-4e1d-a72a-d3cffdfa077f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

/sda is a SATA 160 HDD.

I've modified the boot order since then. Would that make a difference to the output from that the boot_info script? This output was taken before I changed the boot order.

Dp.

---

### Post by presence1960 on 2009-10-07
> **novice buntu said:**
> 

You said install grub on the MBR of /sdd. Does the code snippet you supplied do that or is there another step to get the MBR pointing to the correct root drive?

find /grub/stage2 returned (hd3,0)
Should I then set root as (h3,1) as my / (root partition) is on /dev/sdd2. Assuming grub is indexing the partitions from 0 (zero).


Yes I do want to keep this drive on-line permanently. It has a lot of data on.

I appreciate what your saying about the Windoze partition. I expect that will be easily fixed by editing the menu.lst and a bit of trial and error.

Thanx for you help so far. I don't think I'm that far away from getting this fixed.
Dp.

I would do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd3,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd3,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd3)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```
I believe you want to use root (hd3,0) because that is where your menu.lst is located. For the GRUB menu to come up GRUB must point to menu.lst.  Then when you select Ubuntu from the GRUB menu it will point to your ubuntu partition & boot Ubuntu. Remember you made a separate boot partition!

After doing this and rebooting it is imperative that you get your BIOS hard disk boot order correct. You want this exact order sdd, sdb, sda, sdc. sdb is second because it has windows on it. 

Once you get this sorted out boot into ubuntu, edit your windows entry in menu.lst to this:
```

title           Windows <your version>
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by novice buntu on 2009-10-07
Here's my output from the grub work. I'll have to post again with the outcome of all the operations. It looks good initially.


```
grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1
 (hd3,0)

grub> root (hd3,0)

grub> setup (hd3)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd3)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd3) (hd3)1+17 p (hd3,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

```

---

### Post by novice buntu on 2009-10-07
Well bugger-me-backwards, it worked. At least the Ubuntu partition is working. All my disks are available to Ubuntu. My menu.lst doesn't seem to require editing. Here what it looks like at the moment.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

I'm fairly sure I'll be okay from here. 

I want to thank you both for you patience and time. If your ever in my locale (London), I'll buy you a beer.

I guess I am a little disappointed because I have done much of this parrot fashion, and I am not sure I have gained a better understanding of using grub. If you want to offer a parting gift, a url to howto would be good. 

Thanx again for your help.
Dp.

---

### Post by arrange on 2009-10-07
> **presence1960 said:**
> No experimenting necessary, that is why I asked for the order of hard disk booting in BIOS. When using (hdx,y) in GRUB x is determined by the order of hard disk boot in BIOS. 

Before I gave OP instructions on how to set up GRUB, I wanted that info also so I could explain how to edit menu.lst so windows will boot from the GRUB menu once GRUB is set up.

There is no reason to guess or experiment, GRUB is very orderly and detailed. All you need is the correct info to set it up properly.

It would be nice if it worked the way it is documented.

I tested my own HDDs and changed the boot priority of my 2 SATA disks, and after booting into LiveCD I checked via **sudo grub** that the numbering stayed exactly the same as before. And I saw this more times on forums (especially Czech ones, because I spend most time there). In my case Grub seems to honour the number of the SATA plug. But when you have different types of drives attached, it gets more complicated...

Please understand: I don't want to contradict you just for the sake of it - I'd like to know how it really works :)

**novice buntu:** a nice tutorial - [Herman's classics]("http://members.iinet.net/~herman546/p15.html"), but now the new Grub2 is coming out...

---

