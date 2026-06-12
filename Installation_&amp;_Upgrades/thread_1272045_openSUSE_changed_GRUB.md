---
title: "openSUSE changed GRUB"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by djwkd on 2009-09-21
Hello all,
Earlier today (sorry for sounding like a news bulletin) i installed openSUSE on this machine. Worked fine. Booted into windows. Worked fine. Tried to boot into Ubuntu. "Error 15. File Not Found". It was looking for the kernel. So how do i change the grub settings to point to the right kernel (both the RT and generic), and where are they located?

Any more information you need, just ask :)

Thanks SO MUCH in advance, Dominic.

---

### Post by stlsaint on 2009-09-21
post the results of this from terminal

gksudo gedit /boot/grub/menu.lst

post the output of the file here.

---

### Post by louieb on 2009-09-21
Kernels are found in the /boot directory of the installation.  

Heres a very thorough  GRUB  page [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html") 

as far a specifics for your particular installation it would be great if you could download [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  , run and post the RESULTS.TXT 

Don't know if Open Suse uses sudo or where its browser downloads stuff. So here the how to run using a Ubuntu live CD. [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

---

### Post by stlsaint on 2009-09-21
use this to run BootInfo Script....

sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by djwkd on 2009-09-23
Here is the results from RESULTS.TXT

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Recovery:Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfeeb45ff

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,903,599     9,903,537   b W95 FAT32
/dev/sda2    *      9,903,600   156,280,319   146,376,720   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff1bff1b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   459,587,519   459,587,457   7 HPFS/NTFS
/dev/sdb2         459,587,520   488,392,064    28,804,545   5 Extended
/dev/sdb5         459,587,583   487,090,799    27,503,217  83 Linux
/dev/sdb6         487,090,863   488,392,064     1,301,202  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    19,454,714    19,454,652  83 Linux
/dev/sdc2          19,454,715    38,909,429    19,454,715  83 Linux
/dev/sdc3          38,909,430    58,364,144    19,454,715  83 Linux
/dev/sdc4          58,364,145    80,035,829    21,671,685   f W95 Ext d (LBA)
/dev/sdc5          58,364,208    68,854,589    10,490,382  83 Linux
/dev/sdc6          68,854,653    80,035,829    11,181,177  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="18C1-216D" TYPE="vfat" 
/dev/sda2: UUID="76CC023ACC01F4E1" TYPE="ntfs" 
/dev/sdb1: UUID="AEC8DC86C8DC4E69" LABEL="dominic" TYPE="ntfs" 
/dev/sdb5: UUID="3e925066-7f90-4a72-9226-74372377ca15" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="a6e4d0c5-4902-47b2-9599-ad4566dacaeb" 
/dev/sdc1: UUID="cbd86746-dea9-462d-b077-4f92c2269be3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="9f9ff690-8646-4f9b-982c-c6acea1c3d85" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="803d7750-6524-413f-8e34-e39df5c6c8e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="ba768209-c8fe-4a40-acb3-1038f8f089e7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: UUID="558f4bef-3808-44a3-a709-9ccfcca9401e" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
tmpfs on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /media/cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS.0="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3e925066-7f90-4a72-9226-74372377ca15

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=3e925066-7f90-4a72-9226-74372377ca15 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        3e925066-7f90-4a72-9226-74372377ca15
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=3e925066-7f90-4a72-9226-74372377ca15 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a6e4d0c5-4902-47b2-9599-ad4566dacaeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 248.7GB: boot/grub/menu.lst
 248.7GB: boot/grub/stage2
 248.6GB: boot/initrd.img-2.6.28-11-generic
 248.8GB: boot/initrd.img-2.6.28-15-generic
 248.7GB: boot/initrd.img-2.6.28-3-rt
 248.6GB: boot/vmlinuz-2.6.28-11-generic
 248.7GB: boot/vmlinuz-2.6.28-15-generic
 248.6GB: boot/vmlinuz-2.6.28-3-rt
 248.8GB: initrd.img
 248.7GB: initrd.img.old
 248.7GB: vmlinuz
 248.6GB: vmlinuz.old

=========================== sdc5/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Mon Sep 21 19:16:12 BST 2009
default 0
timeout 8
gfxmenu (hd2,4)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1
    root (hd2,4)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-Maxtor_4D040H2_D25RS9VE-part5 resume=/dev/disk/by-id/ata-WDC_WD2500JB-22GVC0_WD-WCAL74754251-part6 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)###
title Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)
    root (hd1,4)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1
    root (hd2,4)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-Maxtor_4D040H2_D25RS9VE-part5 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default

=============================== sdc5/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD2500JB-22GVC0_WD-WCAL74754251-part6 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-Maxtor_4D040H2_D25RS9VE-part5 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-Maxtor_4D040H2_D25RS9VE-part6 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/ata-WDC_WD800EB-11DJF0_WD-WCAHL3252427-part2 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD2500JB-22GVC0_WD-WCAL74754251-part1 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-WDC_WD800EB-11DJF0_WD-WCAHL3252427-part1 /windows/E           vfat       users,gid=users,umask=0002,utf8=true 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdc5: Location of files loaded by Grub: ===================


  30.8GB: boot/grub/menu.lst
  30.9GB: boot/grub/stage2
  30.8GB: boot/initrd
  30.8GB: boot/initrd-2.6.27.7-9-default
  30.9GB: boot/vmlinuz
  30.9GB: boot/vmlinuz-2.6.27.7-9-default
```

---

### Post by louieb on 2009-09-23
Open Suse's Ubuntu entry is is trying to load Ubuntu's  Grub menu. Thats what the configfile command does. Are you getting the Ubuntu Grub menu?

The Open Suse Ubuntu entry

```
###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)###
title Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)
    root (hd1,4)
    configfile /boot/grub/menu.lst
```Guessing grub is confused about the boot order and looking on the wrong hard drive. So just try all 3 to find the one that works. One of these should work 
```

title Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)
       configfile (hd1,4)/boot/grub/menu.lst
``````

title Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)
        configfile (hd2,4)/boot/grub/menu.lst
``````

title Ubuntu 9.04, kernel 2.6.28-15-generic (/dev/sdb5)
        configfile (hd0,4)/boot/grub/menu.lst
```

---

### Post by dspisak on 2009-09-26
Hello.  You may want to try this method.  It works for me.  (Thanks to Iswest for the solution).

Boot to the Ubuntu LiveCD and then start a terminal (applications/accessories/terminal) and type
Code:
[I]sudo grub
find /boot/grub/stage1
root (hd?,?) e.g. (hd0,1)		
setup (hd?) e.g. (hd0)
quit[/I]

Where the (hd?,?) and (hd?) correspond to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).

---

### Post by louieb on 2009-09-26
> **dspisak said:**
> Hello.  You may want to try this method....

Thats the normal method to get GRUB at boot. Its booting GRUB its just that its in the Open Suse install. And he is trying to get it to boot Ubuntu. 

There are 2 stage2 files. One for Open Suse (hd2,4) and one for Ubuntu (hd1,4).   He could use this method to change it to boot to Ubuntu's GRUB by using (hd1,4) in the root command. 

He hasn't post back in a couple of days - wonder if its booting both now. In particular wonder if he got Open Suse's GRUB to load Ubuntu's GRUB menu. Don't know if Open Suse's GRUB understands what to do with the UUID statement.   If thats the case then he will have to use the method you described.

---

