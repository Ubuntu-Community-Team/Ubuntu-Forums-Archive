---
title: "sytem not loading - error at grub stage after switching off harddrive"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by noteviljoe on 2009-05-17
I recently installed ubuntu using a 8.1 CD on to my fujitsu pc with windows vista - I installed it for dual boot.

Rather stupidly I forgot to turn off my external hard drive and when creating the partition for ubuntu and windows. So it installed ubuntu onto my external harddrive (500GB) - will only start with external harddrive turned on.

I then upgraded, via web, to unbuntu 9.

I was trying to play some music files (all located on the external hardrive) they weren't working. Without thinking I turned off the external hardrive - this made the system crash and not start up again when I turned it back on.

I then turned it off - but now when I try to get it to start up I get
GRUB stage 1.5
error 21

I have now started up the computer using the original live CD. This only works with the external hard drive on.

I want to reinstall ubuntu - without losing windows - without it installing onto the external hard drive - and without losing the data on the external harddrive (most mp3s).

Given that the live cd will only work with the external hardrive on if I then install ubuntu again won't I just end up with it on the external harddrivw](*,)

---

### Post by noteviljoe on 2009-05-17
I saw another post [http://ubuntuforums.org/showthread.php?t=1151743&highlight=GRUB+stage+1.5+error+2]("http://ubuntuforums.org/showthread.php?t=1151743&highlight=GRUB+stage+1.5+error+2")
 asking someone with a booting problem to download boot info script so I've done it the results are:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9887150a

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   389,464,063   364,886,016   7 HPFS/NTFS
/dev/sda4         393,560,064   488,394,751    94,834,688   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1018 MB, 1018167296 bytes
2 heads, 63 sectors/track, 15782 cylinders, total 1988608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0184fc04

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             32     1,988,607     1,988,576   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="22E06592E0656CCB" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="90FC68A2FC688476" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="4EDC6C91DC6C74DD" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdh1: SEC_TYPE="msdos" LABEL="DISK_IMG" UUID="0184-FC04" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdh1 on /media/DISK_IMG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by noteviljoe on 2009-05-17
Bizarrely I have just tried it again, gaining hope after a couple of glasses of wine and --- it booted up fine???? 

Is it a problem with my external hard drive?

I have run the boot info script thingy again and now I get
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9887150a

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   389,464,063   364,886,016   7 HPFS/NTFS
/dev/sda4         393,560,064   488,394,751    94,834,688   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x548c3cb9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   436,630,634   436,630,572   c W95 FAT32 (LBA)
/dev/sdb2         436,630,635   976,768,064   540,137,430   5 Extended
/dev/sdb5         436,630,698   970,727,624   534,096,927  83 Linux
/dev/sdb6         970,727,688   976,768,064     6,040,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="22E06592E0656CCB" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="90FC68A2FC688476" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda4: UUID="4EDC6C91DC6C74DD" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: LABEL="FREECOM HDD" UUID="1AE1-2B56" TYPE="vfat" 
/dev/sdb5: UUID="c6d34156-215a-4afa-9efc-69a2ac30efe5" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="f763e76e-b1f0-4fcb-8a00-eec0754be054" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joseph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joseph)
/dev/sdb1 on /media/FREECOM HDD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
# kopt=root=UUID=c6d34156-215a-4afa-9efc-69a2ac30efe5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c6d34156-215a-4afa-9efc-69a2ac30efe5

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
```

Any one have any clue what happened? The external harddrive must have been working through out as when I loaded the live CD I could access the files on it - so what changed?

Also I would still like to reinstall ubuntu on to the internal hard drive but I am worried that I will mess up windows etc. and I have no CD for it (why do people sell computers with windows but no windows cd??) - anyone got any ideas how I can do this?

---

### Post by Greyfox_75 on 2009-05-17
Is ubuntu installed to the external or just grub? If its just grub I would recommend grabbing a live cd, remove the external, and follow this howto [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by noteviljoe on 2009-05-17
> **Greyfox_75 said:**
> Is ubuntu installed to the external or just grub? If its just grub I would recommend grabbing a live cd, remove the external, and follow this howto [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I would guess that all of ubuntu is installed on the external drive, as it was when i switched off the external that the whole thing crashed. How would I tell?

---

### Post by Greyfox_75 on 2009-05-17
What is the output of "sudo fdisk -l" and "df -h"

---

### Post by noteviljoe on 2009-05-17
output of "sudo fdisk -l"

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9887150a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       24244   182443008    7  HPFS/NTFS
/dev/sda4           24498       30402    47417344    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x548c3cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27179   218315286    c  W95 FAT32 (LBA)
/dev/sdb2           27180       60801   270068715    5  Extended
/dev/sdb5           27180       60425   267048463+  83  Linux
/dev/sdb6           60426       60801     3020188+  82  Linux swap / Solaris
```

Output of df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             251G   41G  198G  18% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  188K  501M   1% /dev
tmpfs                 501M  512K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             209G  208G  158M 100% /media/FREECOM HDD
```

---

### Post by Greyfox_75 on 2009-05-17
Okay yeah your right Ubuntu is on the 500GB drive (/dev/sda5 is mounted to /)

Well if you would still like to install Ubuntu to the internal drive then I would recommend grabbing clonezilla and making a backup of your windows partition first. 

[http://sourceforge.net/project/showfiles.php?group_id=115473&package_id=221066](http://sourceforge.net/project/showfiles.php?group_id=115473&package_id=221066)

You've got at least 198GB open on your external so unless your windows drive is very full you should be able to fit the compressed backup on your external.  Then give the Ubuntu install a try and see if it can manage to resize your Windows partitions correctly.  If it screws up your Windows at least you will have the backup to fall back on.

---

### Post by noteviljoe on 2009-05-18
Thanks, once I've finished the ton of work I need to use computer for I've give it a try.

---

### Post by Mark Phelps on 2009-05-18
Since your internal drive is fully formatted, you're not going to be able to add anymore primary partitions, so I would do the following:
1) Shrink the Vista OS partition -- use the Vista Disk Management tool, not Ubuntu LiveCD or GParted LiveCD
2) Move any data you want to keep off the last NTFS partition onto the Vista partition
3) Remove the last NTFS partition
4) Replace that last partition with an Extended partition using GParted
5) Install Ubuntu to the extended partition

---

### Post by techrascal on 2009-06-05
i am having dual boot of ubuntu8.10 with vista in my compaq notebook....
ubuntu is installed in the external hard drive .....
it does not boot without ext hdd.....
when i boot up with ext hdd connected to notebook i get grub error21 in stage 1.5.....but the system boots after ctrl+alt+del......n the os works fine....
the following is my results.txt file

---

