---
title: "Grub Error 2 after 9.04 install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by WildeBeest on 2009-04-24
I attempted to install Jaunty over a Gutsy install.
The disk has 4 primary partitions on it.

sdb1 - Gutsy
sdb2 - swap
sdb3 - openSUSE 10.3
sdb5 - Hardy
sdb6 - FAT32

Did the manual install option. All seemed to go well, after a restart I got Grub Error 2.

How do I fix this and recover my other installs?

I booted the 9.04 live CD again, selected the install option and step 4 showed:

sdb1 - Jaunty
sdb2 - swap
sdb3 - openSUSE 10.3
sdb5 - Hardy
sdb6 - FAT32

OK, so the other installs are still there, how do I fix gthe MBR and grub?

---

### Post by WildeBeest on 2009-04-24
bump, for some help

---

### Post by WildeBeest on 2009-04-24
From this thread [http://ubuntuforums.org/showthread.php?t=1131191](http://ubuntuforums.org/showthread.php?t=1131191) it was recommended that I run 

sudo bash ~/Desktop/boot_info_script*.sh

This is the contents of RESULTS.txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 218599208 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:   Welcome to openSUSE 10.3 
                       (i586) - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 372868713.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x59905990

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   266,245,244   266,245,182   7 HPFS/NTFS
/dev/sda2         266,246,144   776,798,383   510,552,240   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c16b9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   117,194,174   117,194,112  83 Linux
/dev/sdb2         117,194,175   121,194,359     4,000,185  82 Linux swap / Solaris
/dev/sdb3         121,194,360   247,031,504   125,837,145  83 Linux
/dev/sdb4         247,031,505   625,137,344   378,105,840   5 Extended
/dev/sdb5         247,031,568   372,868,649   125,837,082  83 Linux
/dev/sdb6         372,868,713   625,137,344   252,268,632   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059841

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,794,175    15,794,113   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3E70C06B70C02B89" LABEL="XP Pro" TYPE="ntfs" 
/dev/sda2: UUID="D0F44261F44249C4" LABEL="MS Vista" TYPE="ntfs" 
/dev/sdb1: UUID="11b81795-4d59-40ae-8006-2256fb514698" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="38e5d9c4-c72a-4530-b895-25158af2b1c7" TYPE="swap" 
/dev/sdb3: UUID="9936dcaa-89eb-4844-8faf-dfcec2b8340b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="b7b9a14b-d317-43bf-81a7-8bba791561b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="47DA-F26F" TYPE="vfat" 
/dev/sdc1: LABEL="CORSAIR" UUID="A878-5088" TYPE="vfat" 

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
/dev/sdc1 on /media/CORSAIR type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=11b81795-4d59-40ae-8006-2256fb514698 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=11b81795-4d59-40ae-8006-2256fb514698

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
root        (hd0,0)
uuid        11b81795-4d59-40ae-8006-2256fb514698
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=11b81795-4d59-40ae-8006-2256fb514698 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
uuid        11b81795-4d59-40ae-8006-2256fb514698
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=11b81795-4d59-40ae-8006-2256fb514698 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
uuid        11b81795-4d59-40ae-8006-2256fb514698
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Pro/Vista
root        (hd1,0)
makeactive
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1



title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

title openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=0x31a resume=/dev/sda2 splash=silent showopts
    initrd /boot/initrd-2.6.22.17-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.17-0.1-default



=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=11b81795-4d59-40ae-8006-2256fb514698 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=38e5d9c4-c72a-4530-b895-25158af2b1c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  42.6GB: boot/grub/menu.lst
  42.6GB: boot/grub/stage2
  42.8GB: boot/initrd.img-2.6.28-11-generic
  42.7GB: boot/vmlinuz-2.6.28-11-generic
  42.8GB: initrd.img
  42.7GB: vmlinuz

=========================== sdb3/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Tue Feb 17 17:47:32 EST 2009
default 2
timeout 10
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3 - 2.6.22.19-0.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.19-0.2-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=0x31a resume=/dev/sda2 splash=silent showopts
    initrd /boot/initrd-2.6.22.19-0.2-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3 - 2.6.22.19-0.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.19-0.2-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.19-0.2-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sda1)###
title Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sda1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: linux-2.6.22.17-0.1-default###
title openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=0x31a resume=/dev/sda2 splash=silent showopts
    initrd /boot/initrd-2.6.22.17-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe-2.6.22.17-0.1-default###
title Failsafe -- openSUSE 10.3 - 2.6.22.17-0.1
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.17-0.1-default

=============================== sdb3/etc/fstab: ===============================

/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part2 swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdb3: Location of files loaded by Grub: ===================


 111.9GB: boot/grub/menu.lst
 111.9GB: boot/grub/stage2
 111.9GB: boot/initrd
 111.9GB: boot/initrd-2.6.22.19-0.2-default
 111.9GB: boot/vmlinuz
 111.9GB: boot/vmlinuz-2.6.22.19-0.2-default

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd1,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b455e2b0-04c8-4072-b86b-051aa50228b5 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b455e2b0-04c8-4072-b86b-051aa50228b5 ro single 
initrd        /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title        openSUSE 10.3 - 2.6.22.17-0.1 (on /dev/sdb3)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=0x31a resume=/dev/sda2 splash=silent showopts 
initrd        /boot/initrd-2.6.22.17-0.1-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title        Failsafe -- openSUSE 10.3 - 2.6.22.17-0.1 (on /dev/sdb3)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.22.17-0.1-default root=/dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA310RC04EMWC-part3 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd        /boot/initrd-2.6.22.17-0.1-default
savedefault
boot


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=b7b9a14b-d317-43bf-81a7-8bba791561b9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=38e5d9c4-c72a-4530-b895-25158af2b1c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# VFAT
# FAT32 ~ Linux calls FAT32 file systems vfat)
# /dev/hda1
/dev/sdb6 /media/Share_disk vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 182.9GB: boot/grub/menu.lst
 183.0GB: boot/grub/stage2
 183.0GB: boot/initrd.img-2.6.24-16-generic
 183.0GB: boot/initrd.img-2.6.24-16-generic.bak
 183.0GB: boot/initrd.img-2.6.24-18-generic
 183.0GB: boot/initrd.img-2.6.24-18-generic.bak
 183.0GB: boot/initrd.img-2.6.24-19-generic
 183.0GB: boot/initrd.img-2.6.24-19-generic.bak
 183.0GB: boot/initrd.img-2.6.24-21-generic
 183.0GB: boot/initrd.img-2.6.24-21-generic.bak
 183.1GB: boot/initrd.img-2.6.24-22-generic
 183.0GB: boot/initrd.img-2.6.24-22-generic.bak
 183.0GB: boot/initrd.img-2.6.24-23-generic
 183.1GB: boot/initrd.img-2.6.24-23-generic.bak
 183.0GB: boot/vmlinuz-2.6.24-16-generic
 183.1GB: boot/vmlinuz-2.6.24-18-generic
 183.0GB: boot/vmlinuz-2.6.24-19-generic
 183.1GB: boot/vmlinuz-2.6.24-21-generic
 183.0GB: boot/vmlinuz-2.6.24-22-generic
 183.1GB: boot/vmlinuz-2.6.24-23-generic
 183.0GB: initrd.img
 183.1GB: initrd.img.old
 183.1GB: vmlinuz
 183.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by OlineSixtyOne on 2009-04-24
Make sure your BIOS is set to boot from the hard drive that you installed Jaunty to.

---

### Post by WildeBeest on 2009-04-24
It is, BIOS has not been changed.

---

### Post by meierfra. on 2009-04-24
Maybe the Jaunty grub got installed on your Window drive, and you are still booting with the old Gutsy grub. (that would explain error 2) Try this in a terminal in the LiveCD:

Install the Jaunty grub to the MBR of the Jaunty drive

```
sudo grub
```
and at the  "grub>" prompt:
```

root (hd1,0)
setup (hd1)
quit
```


Reinstall a Windows type MBR to the Windows drive:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot and see whether you are now able to boot into Jaunty.

---

### Post by WildeBeest on 2009-04-24
Thanks, I'll give it a try in about a hour.

---

### Post by WildeBeest on 2009-04-24
Thanks meierfra, that worked.
Now I have to get my windows boot loader. I know how to do that.

---

### Post by meierfra. on 2009-04-24
> that worked.
Great.

> Now I have to get my windows boot loader. 
???
The entry you have on menu.lst for Windows should work.
Or is there a problem with the Windows boot loader?

If you would like, I can show you  how to separate the XP and Vista boot loader, so that you can boot all your OSs directly from Grub menu (without having to go through the Windows boot menu)

You might also consider chain loading  Suse and Hardy, so that you don't have to edit your Jaunty menu.lst after Suse/Hardy kernel updates.

---

