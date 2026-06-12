---
title: "Grub no longer gives option for Windows XP"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by AdequateRemedy on 2008-12-31
Ok, about a week ago I installed ubuntu on my computer (previously only windows xp). However, today I was trying to mess with the partitions and ending up screwing everything up. Long story short I ended up with only ubuntu on my computer and completely re-installed windows xp. Once I got windows up and running whenever I restarted my computer just went into windows without any other option. So I googled the problem and figured about how to fix it and reinstall grub in the mbr. However, now while grub loads and I can get into Ubuntu, grub doesn't give me an option to go into windows xp, and I'm at a loss as to how to fix it. 

In googling the problem I came across a similar post on these forums, and in order to address the problem someone asked for the results of the command 
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

So I have attached that below in case it helps anyone. 

> ============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 161597835.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   161597834    80798886   83  Linux
/dev/sda2   *   161597835   304961894    71682030    7  HPFS/NTFS
/dev/sda3       315629055   321669494     3020220    5  Extended
/dev/sda5       315629118   321669494     3020188+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="98a3474e-fd0d-4f97-a08b-99dfe17b5812" TYPE="ext3" 
/dev/sda2: UUID="5870FE8570FE6960" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="4bb0e51d-5d16-4898-9cda-f42ad6a20e83" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/caroline/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=caroline)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=98a3474e-fd0d-4f97-a08b-99dfe17b5812 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98a3474e-fd0d-4f97-a08b-99dfe17b5812

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
uuid		98a3474e-fd0d-4f97-a08b-99dfe17b5812
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=98a3474e-fd0d-4f97-a08b-99dfe17b5812 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		98a3474e-fd0d-4f97-a08b-99dfe17b5812
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=98a3474e-fd0d-4f97-a08b-99dfe17b5812 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		98a3474e-fd0d-4f97-a08b-99dfe17b5812
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98a3474e-fd0d-4f97-a08b-99dfe17b5812 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4bb0e51d-5d16-4898-9cda-f42ad6a20e83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2008-12-30 08:49 .
drwxr-xr-x 20 root root    4096 2008-12-30 19:23 ..
-rw-r--r--  1 root root  507665 2008-10-24 01:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 01:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-30 08:50 grub
-rw-r--r--  1 root root 8178735 2008-12-30 08:49 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 01:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 01:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 01:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2008-12-30 08:50 .
drwxr-xr-x 3 root root   4096 2008-12-30 08:49 ..
-rw-r--r-- 1 root root    197 2008-12-30 08:49 default
-rw-r--r-- 1 root root     15 2008-12-30 08:49 device.map
-rw-r--r-- 1 root root   8108 2008-12-30 08:49 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-30 08:49 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-30 08:49 installed-version
-rw-r--r-- 1 root root   8712 2008-12-30 08:49 jfs_stage1_5
-rw-r--r-- 1 root root   4310 2008-12-30 08:50 menu.lst
-rw-r--r-- 1 root root   7352 2008-12-30 08:49 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-30 08:49 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-30 08:49 stage1
-rw-r--r-- 1 root root 121460 2008-12-30 08:49 stage2
-rw-r--r-- 1 root root   9556 2008-12-30 08:49 xfs_stage1_5

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

---

### Post by logos34 on 2008-12-31
> **AdequateRemedy said:**
> now while grub loads and I can get into Ubuntu, grub doesn't give me an option to go into windows xp, and I'm at a loss as to how to fix it. 

gksudo gedit /boot/grub/menu.lst

Change this:

> hiddenmenu

to this:

> **[COLOR="Blue"]#[/COLOR]**hiddenmenu

Add windows entry to bottom:

> title Windows XP
root (hd0,1) 
makeactive
chainloader +1

---

### Post by AdequateRemedy on 2008-12-31
Haha I knew it would be simple. Thanks so much it works now!

---

### Post by decoherence on 2008-12-31
i'm glad you got a solution! i was just going to say "good for grub!" :lolflag:

you can thank logos34 by clicking the medal icon in the lower right of his/her post.

see you 'round the forums! (hopefully not due to problems, tho! :D)

---

