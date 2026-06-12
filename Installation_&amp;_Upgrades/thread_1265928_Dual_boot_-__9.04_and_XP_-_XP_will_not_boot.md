---
title: "Dual boot -  9.04 and XP - XP will not boot"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by jdstunner on 2009-09-14
Hello all and thank you for looking at this post!

I have installed a dual boot system with Ubuntu and XP several times. However, the last two times I have installed this configuration, I have not been able to get XP to boot. I have a complex drive configuration that I believe is causing my issues. I have gone over many threads and looked at all possible configuration files. I cannot figure out where I'm screwed up here.

I have reinstalled XP and Ubuntu too many times to do this again! I need to be able to configure this setup properly without reinstalling any OS.

I am running 3 different hard drives.

/dev/sda1 = 120 GB hard disk, fat32, extra storage
/dev/sdb1 = 20 GB, ext3, ubuntu 8.04
/dev/sdb2 = 4 GB, swap
/dev/sdb3 = 900 GB, ext3, media storage
/dev/sdc1 = 80 GB, ntfs, win XP
/dev/sdc2 =80 GB, ext3, ubuntu 9.04

Here is the idea behind this madness:
sda for program files and data
sdb is a 1 TB media drive... There is 8.04 installed here so I can pull the media drive out and boot it standalone from any PC.
sdc is a 160GB drive with two 80 GB partitions; linux and xp

9.04 uses the swap partition on sdb2

I had XP running smooth! After installing 9.04 to sdc2, I cannot get XP to boot any longer. I get this error:

[I]Starting up...
This is not a bootable disk. Please enter a bootable floppy and press any key to try again...[/I]


```

jim@lnxdsktp:~$ sudo fdisk -l
[sudo] password for jim: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000523f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        2918     3903795   82  Linux swap / Solaris
/dev/sdb3            2919      121601   953321197+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ea02e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS
/dev/sdc2            9729       19457    78148192+  83  Linux

``````

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```ALL HELP IS MOST APPRECIATED!!! THANK YOU!

---

### Post by jdstunner on 2009-09-14
I was looking at another thread and *louieb *posted a link to [this boot script]("http://sourceforge.net/projects/bootinfoscript"). Here are the results. I am definitely no expert on grub or the windows boot loader or the MBR. It is about time for me to learn!

After downloading, run

```

sudo bash ~/Desktop/boot_info_script*.sh

```

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00010b2c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   234,436,544   234,436,482   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000523f8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080    46,877,669     7,807,590  82 Linux swap / Solaris
/dev/sdb3          46,877,670 1,953,520,064 1,906,642,395  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ea02e9f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sdc2         156,280,320   312,576,704   156,296,385  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="53E3-EBFA" TYPE="vfat" 
/dev/sdb1: UUID="65d4b91f-fea1-43b8-aaf0-d891300444c9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="d9503515-5f4f-41d7-815e-98e323971399" TYPE="swap" 
/dev/sdb3: LABEL="mediadrive" UUID="5c1925bf-71f5-4218-a99b-41d72ae0440d" TYPE="ext3" 
/dev/sdc1: UUID="E4D47786D4775A2E" TYPE="ntfs" 
/dev/sdc2: UUID="40f69a3e-9ce9-4e11-a2e4-4121cd845973" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdc2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /data type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb3 on /mediadrive type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jim)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=5c1925bf-71f5-4218-a99b-41d72ae0440d /mediadrive     ext3    relatime        0       2
# /dev/sda2
UUID=d9503515-5f4f-41d7-815e-98e323971399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.0GB: boot/grub/menu.lst
   4.1GB: boot/grub/stage2
   4.0GB: boot/initrd.img-2.6.24-23-generic
   4.0GB: boot/initrd.img-2.6.24-23-generic.bak
   4.1GB: boot/initrd.img-2.6.24-24-generic
   4.0GB: boot/initrd.img-2.6.24-24-generic.bak
   4.1GB: boot/vmlinuz-2.6.24-23-generic
   4.1GB: boot/vmlinuz-2.6.24-24-generic
   4.1GB: initrd.img
   4.0GB: initrd.img.old
   4.1GB: vmlinuz
   4.1GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=40f69a3e-9ce9-4e11-a2e4-4121cd845973

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        40f69a3e-9ce9-4e11-a2e4-4121cd845973
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=65d4b91f-fea1-43b8-aaf0-d891300444c9 ro single 
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.2, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc2 during installation
UUID=40f69a3e-9ce9-4e11-a2e4-4121cd845973 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda1 during installation
UUID=53E3-EBFA  /data           vfat    utf8,umask=007,gid=46 0       1
# /mediadrive was on /dev/sdb3 during installation
UUID=5c1925bf-71f5-4218-a99b-41d72ae0440d /mediadrive     ext3    relatime        0       2
# swap was on /dev/sdb2 during installation
UUID=d9503515-5f4f-41d7-815e-98e323971399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


 149.1GB: boot/grub/menu.lst
 149.1GB: boot/grub/stage2
 149.2GB: boot/initrd.img-2.6.28-11-generic
 149.2GB: boot/vmlinuz-2.6.28-11-generic
 149.2GB: initrd.img
 149.2GB: vmlinuz

```

---

### Post by jdstunner on 2009-09-14
I ran my XP installation CD and logged onto the Recovery Console.

Running

```
fixmbr
```

solved my XP boot problem. 

I can now log onto XP. I'm using it right now. :(

I now need to reinstall grub and get everything running smoothly. How do I get this to work right? What am I missing??

---

### Post by jdstunner on 2009-09-14
Sorry for multiple posts... please refer to thread

[http://ubuntuforums.org/showthread.php?p=7948075#post7948075](http://ubuntuforums.org/showthread.php?p=7948075#post7948075)

---

### Post by presence1960 on 2009-09-14
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd2,1) (hd1,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd2,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd2)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd2)**
```

This will put GRUB on MBR of sdc. Reboot & go into BIOS and set your hard disk boot order like this: 160 GB, 1 TB, 120 GB. Save changes to CMOS and reboot. Boot into Ubuntu 9.04 and open a terminal and run this command: ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

Edit your windows entry to look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
chainloader    +1
```

When using (hdx,y) it is the disk boot order in BIOS that determines the x(device) setting because that is the actual order of how the disks load. Since sdc is set to boot first it is actually (hd0). You only need map commands when windows is not on the first disk which boots. So you don't need them here.

I would also remove all those entries for Hard y and chainload it like this:

```
title         Ubuntu 8.04
rootnoverify  (hd1,0)
chainloader   +1
 

```

You can put hardy's chainload entry before or after windows entry. Click save on the toolbar at top, close the file & reboot. You should be good to go.

---

### Post by jdstunner on 2009-09-14
You are the man! I've been having trouble with this for a long time. I have talked to several different people. Make this post as solved. 

Thank you.:guitar:

---

### Post by jdstunner on 2009-09-14
> **jdstunner said:**
> You are the man! I've been having trouble with this for a long time. I have talked to several different people. Make this post as solved. 

Thank you.:guitar:


I spoke too soon. My Hardy install won't chainload.

I made entries in menu.lst like this:

[I]title         Ubuntu 8.04
rootnoverify  (hd1,0)
chainloader   +1 [/I]

and it wouldn't boot. So I edited grub like this:

[I]sudo grub
root (hd1,0)
setup (hd1)
quit
[/I]
Still no luck. Jaunty and XP work good. This is sdb we are talking about here. It is second on the BIOS boot order and second in grub-speak. So it should be hd1 no matter what.

---

### Post by presence1960 on 2009-09-14
> **jdstunner said:**
> I spoke too soon. My Hardy install won't chainload.

I made entries in menu.lst like this:

[I]title         Ubuntu 8.04
rootnoverify  (hd1,0)
chainloader   +1 [/I]

and it wouldn't boot. So I edited grub like this:

[I]sudo grub
root (hd1,0)
setup (hd1)
quit
[/I]
Still no luck. Jaunty and XP work good. This is sdb we are talking about here. It is second on the BIOS boot order and second in grub-speak. So it should be hd1 no matter what.

Just to be sure open a terminal from 9.04 and run this:
sudo grub

grub> find /boot/grub/stage1

report back what that last command displays.

---

### Post by jdstunner on 2009-09-14
hd(1,0)
hd(2,1)

---

### Post by presence1960 on 2009-09-14
> **jdstunner said:**
> hd(1,0)
hd(2,1)

The (hd1,0) is the one for hardy. What error do you get when you choose hardy on boot?

---

### Post by presence1960 on 2009-09-14
I have to go to my part time job now. Will be back on in 4 hours or so.

---

### Post by jdstunner on 2009-09-14
Im not sitting at that PC at the moment... I'm 90% sure it said:

*Error 13: File not Found*

---

