---
title: "Grub menu.lst question"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Erszebet Lunah on 2009-01-07
Hi all,

I'm almost ashamed to post this here, 'cause there's quite a lot of information on this topic already but I just can't figure this little problem out on my own :(

I wanted to install Kubuntu 8.10 yesterday, using the alternative CD because I'm using a Sata RAID1.
What I wanted was a dual boot system (Kubuntu & Windows). For Linux I have a separate disk (80 GB IDE) connected to Primary master, which also is the primary boot device in my BIOS. Windows was pre-installed on the RAID.

The installer did recognize the RAID and asked to activate it (answered 'yes').
But after rebooting Grub naturally didn't list Windows as a possible OS.
Here's my original menu.lst:

```

...
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8460684-ae17-4637-92f3-730e55dae96f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8460684-ae17-4637-92f3-730e55dae96f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
...

```

I've searched this forums for quite some time and finally found and added an entry for Windows in menu.lst, like this:
```

title		Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

```

But that doesn't work. I get a very tiny look of the Windows screensaver popping up, immediately followed by a BSOD (serieus error, have to reboot, no recovery possible). I also tried with (hd2) & (hd0) - combinations for map, but to no avail.
Weird thing is, if I go to my BIOS and change the order of HD's to boot from (set RAID as primary) it loads Windows just fine. Ofcourse, I don't have a choice which OS to boot then :p

Here's the output from sudo fdisk -lu:
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0xffffffff                                          

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75778604    37889271    7  HPFS/NTFS
/dev/sda2        75778605   390700799   157461097+   f  W95 Ext'd (LBA)
/dev/sda5        75778668   200700044    62460688+   7  HPFS/NTFS      
/dev/sda6       200700108   264188924    31744408+   b  W95 FAT32      
/dev/sda7       264188988   327677804    31744408+   b  W95 FAT32      
/dev/sda8       327677868   390700799    31511466    b  W95 FAT32      

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes                               
Disk identifier: 0xffffffff                                          

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    75778604    37889271    7  HPFS/NTFS
/dev/sdb2        75778605   390700799   157461097+   f  W95 Ext'd (LBA)
/dev/sdb5        75778668   200700044    62460688+   7  HPFS/NTFS
/dev/sdb6       200700108   264188924    31744408+   b  W95 FAT32
/dev/sdb7       264188988   327677804    31744408+   b  W95 FAT32
/dev/sdb8       327677868   390700799    31511466    b  W95 FAT32

Disk /dev/sdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde1f2bf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   150368399    75184168+  83  Linux
/dev/sdc2       150368400   156360644     2996122+   5  Extended
/dev/sdc5       150368463   156360644     2996091   82  Linux swap / Solaris


```

This is what device.map has:
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

So basically what I want is Grub to recognize and load Windows OS. I got everything installed as I want but can't dual boot and have little understanding of Grub commands...

---

### Post by Erszebet Lunah on 2009-01-07
Forgot to post this too, output from a script I've seen people use here:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sda6 already mounted or sda6 busy

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sda7 already mounted or sda7 busy

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sda8 already mounted or sda8 busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb6 already mounted or sdb6 busy

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb7 already mounted or sdb7 busy

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb8 already mounted or sdb8 busy

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75778604    37889271    7  HPFS/NTFS
/dev/sda2        75778605   390700799   157461097+   f  W95 Ext'd (LBA)
/dev/sda5        75778668   200700044    62460688+   7  HPFS/NTFS
/dev/sda6       200700108   264188924    31744408+   b  W95 FAT32
/dev/sda7       264188988   327677804    31744408+   b  W95 FAT32
/dev/sda8       327677868   390700799    31511466    b  W95 FAT32

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    75778604    37889271    7  HPFS/NTFS
/dev/sdb2        75778605   390700799   157461097+   f  W95 Ext'd (LBA)
/dev/sdb5        75778668   200700044    62460688+   7  HPFS/NTFS
/dev/sdb6       200700108   264188924    31744408+   b  W95 FAT32
/dev/sdb7       264188988   327677804    31744408+   b  W95 FAT32
/dev/sdb8       327677868   390700799    31511466    b  W95 FAT32

sfdisk -V /dev/sdb:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde1f2bf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   150368399    75184168+  83  Linux
/dev/sdc2       150368400   156360644     2996122+   5  Extended
/dev/sdc5       150368463   156360644     2996091   82  Linux swap / Solaris

sfdisk -V /dev/sdc:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1E90D88D90D86CB1" LABEL="WinXP" TYPE="ntfs" 
/dev/sda5: UUID="60200843200822A0" LABEL="GAMES" TYPE="ntfs" 
/dev/sda6: LABEL="MUSIC" UUID="4C8C-A2E1" TYPE="vfat" 
/dev/sda7: LABEL="CRASHES" UUID="302F-17E1" TYPE="vfat" 
/dev/sda8: LABEL="DOWNLOAD" UUID="ECE0-D499" TYPE="vfat" 
/dev/sdb1: UUID="1E90D88D90D86CB1" LABEL="WinXP" TYPE="ntfs" 
/dev/sdb5: UUID="60200843200822A0" LABEL="GAMES" TYPE="ntfs" 
/dev/sdb6: LABEL="MUSIC" UUID="4C8C-A2E1" TYPE="vfat" 
/dev/sdb7: LABEL="CRASHES" UUID="302F-17E1" TYPE="vfat" 
/dev/sdb8: LABEL="DOWNLOAD" UUID="ECE0-D499" TYPE="vfat" 
/dev/sdc1: UUID="d8460684-ae17-4637-92f3-730e55dae96f" TYPE="ext3" 
/dev/sdc5: UUID="9f9bbd3f-6b26-42e8-ae53-f71f39d73250" TYPE="swap" 
/dev/mapper/nvidia_hfefgahe1: UUID="1E90D88D90D86CB1" LABEL="WinXP" TYPE="ntfs" 
/dev/mapper/nvidia_hfefgahe5: UUID="60200843200822A0" LABEL="GAMES" TYPE="ntfs" 
/dev/mapper/nvidia_hfefgahe6: LABEL="MUSIC" UUID="4C8C-A2E1" TYPE="vfat" 
/dev/mapper/nvidia_hfefgahe7: LABEL="CRASHES" UUID="302F-17E1" TYPE="vfat" 
/dev/mapper/nvidia_hfefgahe8: LABEL="DOWNLOAD" UUID="ECE0-D499" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d8460684-ae17-4637-92f3-730e55dae96f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d8460684-ae17-4637-92f3-730e55dae96f

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
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8460684-ae17-4637-92f3-730e55dae96f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8460684-ae17-4637-92f3-730e55dae96f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d8460684-ae17-4637-92f3-730e55dae96f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8460684-ae17-4637-92f3-730e55dae96f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9f9bbd3f-6b26-42e8-ae53-f71f39d73250 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 12996
drwxr-xr-x  3 root root    4096 2009-01-06 19:17 .
drwxr-xr-x 20 root root    4096 2009-01-06 18:17 ..
-rw-r--r--  1 root root  503560 2008-11-04 21:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-04 21:53 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-06 19:51 grub
-rw-r--r--  1 root root 8836707 2009-01-06 19:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 21:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-04 21:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2339552 2008-11-04 21:53 vmlinuz-2.6.27-7-generic

=============================== sdc1/boot/grub: ===============================

total 356
drwxr-xr-x 2 root root   4096 2009-01-06 19:51 .
drwxr-xr-x 3 root root   4096 2009-01-06 19:17 ..
-rw-r--r-- 1 root root    197 2009-01-06 18:51 default
-rw-r--r-- 1 root root     45 2009-01-06 18:50 device.map
-rw-r--r-- 1 root root   8108 2009-01-06 18:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-06 18:51 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-06 18:51 installed-version
-rw-r--r-- 1 root root   8712 2009-01-06 18:51 jfs_stage1_5
-rw-r--r-- 1 root root   4312 2009-01-06 19:17 menu.lst
-rw-r--r-- 1 root root   4312 2009-01-06 19:17 menu.lst~
-rw-r--r-- 1 root root   4312 2009-01-06 19:51 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-06 18:51 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-06 18:51 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-06 18:51 stage1
-rw-r--r-- 1 root root 121460 2009-01-06 18:51 stage2
-rw-r--r-- 1 root root 121460 2009-01-06 18:34 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-01-06 18:51 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.


```

You'll see that all partitions on RAID or listed 'already mounted or busy'. I suppose this causes the problem that I can't read or write from those disks in Linux ? If I click on them in Dolphin it just hangs for a second and then switches back to last selected directory. Also the RAID disks are not listed as 1 disk like in Windows.

---

### Post by caljohnsmith on 2009-01-07
I see you actually have Grub installed to the MBR of both the sda and sdc drives. But since you mentioned that you can boot directly into Windows by changing your BIOS to boot your RAID array, then it looks like the sdb drive is being booted in that case. The first thing I would recommend doing is replacing Grub in your sda drive with a Windows MBR, so then there can be no ambiguity which drive you are booting from if you get the Grub menu. So how about doing:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
But about booting Windows from Grub, since you have a RAID array that can make it difficult. How about adding all the following entries to your menu.lst:
```
title       Windows XP (1a)
rootnoverify     (hd1,0)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (1b)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
chainloader +1

title       Windows XP (2a)
rootnoverify     (hd2,0)
map        (hd2) (hd0)
chainloader +1

title       Windows XP (2b)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
chainloader +1


title       Windows XP (2c)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
And let me know exactly what happens when you try each of those from the Grub menu. We can work from there if you want.

---

### Post by Erszebet Lunah on 2009-01-09
Ok, finally got time to test this.
Option (1a) hit the spot from the start and loaded Windows, but I'll give you the other results just for fun :P

(1b) -> Starting up... then hangs
(2a), (2b) and (2c) -> Selected disk does not exist

I haven't replaced grub on sda yet, could that be the problem with Linux not displaying my Raid as 1 drive - 'cos he actually boots the 'mirror-drive' ? (dunno if that makes sense :p )

---

### Post by caljohnsmith on 2009-01-09
> **Erszebet Lunah said:**
> Ok, finally got time to test this.
Option (1a) hit the spot from the start and loaded Windows, but I'll give you the other results just for fun :P

(1b) -> Starting up... then hangs
(2a), (2b) and (2c) -> Selected disk does not exist

I haven't replaced grub on sda yet, could that be the problem with Linux not displaying my Raid as 1 drive - 'cos he actually boots the 'mirror-drive' ? (dunno if that makes sense :p )
Glad to hear that you got Windows to boot OK. About replacing Grub in the MBR of sda, that should not affect how Ubuntu sees your RAID drives. You might want to check out the package "mdadm" in order to get your RAID drives recognized properly.

---

