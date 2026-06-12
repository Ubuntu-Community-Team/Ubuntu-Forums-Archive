---
title: "After Package update, error 24 attempt to access block outsite of partition"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by cddrummergo on 2009-05-06
I was running a Jaunty 9.10 on amd64 with ext4 and it was flying, did a sudo apt-get update, upgrade and got this error message. forgot to say, what the hell was in that last update?

Error 24: attempt to access block outside of partition. 
Press any key to continue. 

Now looking around, I found this post 
[http://www.ubuntuforums.org/showthread.php?t=1135898](http://www.ubuntuforums.org/showthread.php?t=1135898)

 and the person asked to see the results of a boot scan script that came out like this,(code below)

I tried super grub and no luck, also tried editing grub to boot off of /dev/sda3 and no luck. 

Could someone please help me get back online?
Thanks!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
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
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xafdec7e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   107,868,189   107,868,127   7 HPFS/NTFS
/dev/sda2         107,872,255   138,590,207    30,717,953   f W95 Ext d (LBA)
/dev/sda5         107,872,256   138,590,207    30,717,952   7 HPFS/NTFS
/dev/sda3         138,590,208   220,508,159    81,917,952  83 Linux
/dev/sda4         220,508,190   234,436,544    13,928,355  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a6e01

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,477,979     1,477,917   b W95 FAT32
/dev/sdb2           1,477,980     3,903,794     2,425,815  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A64206114205E6C1" TYPE="ntfs" 
/dev/sda3: UUID="41c5f08b-a5bc-4f24-a213-30bfd7f629ca" TYPE="ext4" 
/dev/sda4: UUID="4aca18fa-7caf-4109-adcb-fc6f883a8483" TYPE="swap" 
/dev/sda5: UUID="8C6EB6456EB6283A" LABEL="SwapTemp" TYPE="ntfs" 
/dev/sdb1: UUID="58A4-B439" TYPE="vfat" 
/dev/sdb2: LABEL="casper-rw" UUID="62735f15-97bc-4225-b791-a91d7526a09a" TYPE="ext2" 

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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb2 on /media/casper-rw type ext2 (rw,nosuid,nodev,uhelper=hal)


=========================== sda3/boot/grub/menu.lst: ===========================

splashimage=/boot/grub/h-k-suite-grub.xpm.gz
background FFFFFF
foreground B30C0E
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash vga=792

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
# howmany=3

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro splash vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.26.3-ultimate
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26.3-ultimate root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro splash vga=792 
initrd		/boot/initrd.img-2.6.26.3-ultimate
quiet

title		Ubuntu 9.04, kernel 2.6.26.3-ultimate (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26.3-ultimate root=UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca ro  single
initrd		/boot/initrd.img-2.6.26.3-ultimate

title		Ubuntu 9.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=41c5f08b-a5bc-4f24-a213-30bfd7f629ca /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=2d39d072-a553-4031-aa4c-a7d250fa6ee6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

tmpfs     /dev/shm     tmpfs     defaults,ro     0     0

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)



=================== sda3: Location of files loaded by Grub: ===================


 112.2GB: boot/grub/menu.lst
 112.1GB: boot/grub/stage2
 112.2GB: boot/initrd.img-2.6.26.3-ultimate
 112.2GB: boot/initrd.img-2.6.26.3-ultimate.bak
 112.3GB: boot/initrd.img-2.6.27-11-generic
 112.6GB: boot/initrd.img-2.6.28-11-generic
 112.2GB: boot/vmlinuz-2.6.26.3-ultimate
 112.2GB: boot/vmlinuz-2.6.27-11-generic
 112.2GB: boot/vmlinuz-2.6.28-11-generic
 112.6GB: initrd.img
 112.3GB: initrd.img.old
 112.2GB: vmlinuz
 112.2GB: vmlinuz.old
```

---

### Post by Maximus_Powermus on 2009-05-08
I have the same issue after updating this morning. It appears that something with respect to the initrd is corrupt. I have been able to boot from the grub command line by entering:

root (hd0,0)
kernel /boot/vmlinuz-2.6.28-12-generic root=/dev/sda1 ro quiet splash
quiet
boot

Commenting out the initrd portion of your menu.lst should work also. I am having a different problem after updating also though where grub automatically dumps me to the command line and I can't even load menu.lst using the configfile command. I am using the package maintainer's menu.lst.

---

### Post by Maximus_Powermus on 2009-05-08
I found a fix that worked for me:

[http://mapopa.blogspot.com/2009/01/grub-voodoo-error-no-1324-and-how-do-i.html](http://mapopa.blogspot.com/2009/01/grub-voodoo-error-no-1324-and-how-do-i.html)

Boot from the live cd and:

$ sudo su
# mount /dev/sda1 /mnt
# mount --bind /dev /mnt/dev
# mount --bind /dev/pts /mnt/dev/pts
# mount --bind /dev/shm /mnt/dev/shm
# mount -t proc none /mnt/proc
# mount -t sysfs none /mnt/sys
# chroot /mnt /bin/bash
# grub-install /dev/sda --root-directory=/ --rechec

---

### Post by cddrummergo on 2009-05-08
stops me at the chroot

chroot: cannot run command `/bin/bash': Exec format error
root@ubuntu:/home/ubuntu# 

root@ubuntu:/home/ubuntu# grub-install /dev/sda --root-directory=/ --recheck
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for //boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# 

root@ubuntu:/home/ubuntu# df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   480472      2392    478080   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   480472      2392    478080   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                   480472         0    480472   0% /lib/init/rw
varrun                  480472       108    480364   1% /var/run
varlock                 480472         0    480472   0% /var/lock
udev                    480472       160    480312   1% /dev
tmpfs                   480472       880    479592   1% /dev/shm
rootfs                  480472     36688    443784   8% /
/dev/sdb1               734860    715588     19272  98% /cdrom
/dev/loop0              691328    691328         0 100% /rofs
tmpfs                   480472        12    480460   1% /tmp
/dev/sdb2              1203296      1800   1140852   1% /media/casper-rw
/dev/sda1             40635768  21974516  16613304  57% /mnt
/dev/sda3             40635768  21974516  16613304  57% /mnt
root@ubuntu:/home/ubuntu#

---

