---
title: "Grub installed in wrong place?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by zob on 2009-05-07
Hi all.

I just installed the brand new ubuntu 9.04 i386 on ext4 from the alternate install disk.

I did install at the end of the process. When I boot up, however it's the old windows boot-loader I see, not Grub.

I suspect that grub was installed in the wrong place (I guess that the MBR has to 'see' it somehow - and I don't think it does).

As far as I recall I had a problem with this in the past. Could it be that my BIOS doesn't read MBR from the SATA HD where I installed Ubuntu (but needs a ATA HD for the MBR and therefore installed it elsewhere - see below)?

I do recall that the windows boot-loader is installed on what windows sees as the first HD (but Linux seems to see as the second HD). Whereas Grub was install on what Linux sees as hd0.

I booted into Live CD and did the "sudo grub", "find /boot/grub/stage1"-thing, and got (hd0,2). After that I did "root (hd0,2)" and then setup (hd0) and the quit. But the result is exactly the same - I just get the windows boot-loader.

Here follows the output of "sudo fdisk -l"

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003c58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7017    56364021    7  HPFS/NTFS
/dev/sda2            7018       27764   166650277+   f  W95 Ext'd (LBA)
/dev/sda3   *       27765       30270    20129445   83  Linux
/dev/sda4           30271       30402     1054808+  82  Linux swap / Solaris
/dev/sda5            7018       27764   166650246    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7b1b7b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/sdb5            3825        9729    47431881    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7fe0987

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdc2           12749       17946    41752935    7  HPFS/NTFS
/dev/sdc3           17947       24321    51207187+   f  W95 Ext'd (LBA)
/dev/sdc5           17947       24321    51207156    7  HPFS/NTFS

```

For reference, I'm quite sure that XP reads the bootloader from what is listed above as /dev/sdb1/ (though that is not really where my XP partitions are (I have 2 of them). I think XP is installed on /dev/sda1 and /dev/sdc1. (Ok. It's a mess, I know).

I hope someone can help.

---

### Post by zob on 2009-05-07
I just wanted to add the result.txt that I get from running the boot_info_script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00003c58

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   112,728,104   112,728,042   7 HPFS/NTFS
/dev/sda2         112,728,105   446,028,659   333,300,555   f W95 Ext d (LBA)
/dev/sda5         112,728,168   446,028,659   333,300,492   7 HPFS/NTFS
/dev/sda3    *    446,028,660   486,287,549    40,258,890  83 Linux
/dev/sda4         486,287,550   488,397,166     2,109,617  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7b1b7b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sdb2          61,432,560   156,296,384    94,863,825   f W95 Ext d (LBA)
/dev/sdb5          61,432,623   156,296,384    94,863,762   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7fe0987

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdc2         204,796,620   288,302,489    83,505,870   7 HPFS/NTFS
/dev/sdc3         288,302,490   390,716,864   102,414,375   f W95 Ext d (LBA)
/dev/sdc5         288,302,553   390,716,864   102,414,312   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C2F844E5F844D8F5" LABEL="XPpro" TYPE="ntfs" 
/dev/sda3: LABEL="ubuntu" UUID="38256f3d-cb00-41c4-a766-204c0326e267" TYPE="ext4" 
/dev/sda4: TYPE="swap" 
/dev/sda5: UUID="1260AE862D8BFE31" LABEL="Samples" TYPE="ntfs" 
/dev/sdb1: LABEL="PROGRAMFILE" UUID="4497-37C7" TYPE="vfat" 
/dev/sdb5: UUID="112CCBEE3447F861" LABEL="Musik" TYPE="ntfs" 
/dev/sdc1: UUID="26D076CCD076A1AB" LABEL="XPmusik" TYPE="ntfs" 
/dev/sdc2: UUID="08D04322D043157A" LABEL="Noder&TTC" TYPE="ntfs" 
/dev/sdc5: UUID="5AE46058E4603881" LABEL="DownOgBacku" TYPE="ntfs" 

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


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=38256f3d-cb00-41c4-a766-204c0326e267 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=38256f3d-cb00-41c4-a766-204c0326e267

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		38256f3d-cb00-41c4-a766-204c0326e267
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=38256f3d-cb00-41c4-a766-204c0326e267 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		38256f3d-cb00-41c4-a766-204c0326e267
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=38256f3d-cb00-41c4-a766-204c0326e267 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		38256f3d-cb00-41c4-a766-204c0326e267
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=38256f3d-cb00-41c4-a766-204c0326e267 /               ext4    relatime,errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 230.4GB: boot/grub/menu.lst
 230.4GB: boot/grub/stage2
 232.8GB: boot/initrd.img-2.6.28-11-generic
 228.6GB: boot/vmlinuz-2.6.28-11-generic
 232.8GB: initrd.img
 228.6GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=5

default=c:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Audio" /fastdetect /NoExecute=OptOut

C:\wubildr.mbr = "Ubuntu"


================================ sdb1/BOOT.INI: ================================

[boot loader]

timeout=5

default=c:\wubildr.mbr

[operating systems]

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Audio" /fastdetect /NoExecute=OptOut

C:\wubildr.mbr = "Ubuntu"

```

That wubi-thing at the end should be gone. I deleted that.

---

### Post by zob on 2009-05-07
Sorrryyyyy. I back. It is solved. I found an option in my BIOS to press F11 while booting and then being able to boot from the appropriate HD.

So even though I'll have to do that trick at boot-up if I want another boot-loader than what I choose as default boot-option i BIOS, it's working and fine with me.

---

