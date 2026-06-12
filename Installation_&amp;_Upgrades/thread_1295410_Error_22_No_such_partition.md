---
title: "Error 22: No such partition"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Treepwood on 2009-10-19
Hi

I have been using Ubuntu for some time on a test computer, and decided that I liked it, and now I wanted to install it on my primary computer, but keeping Win XP for gaming.

I had XP installed beforhand, and used a LiveCD to install Unbuntu. This is where my problems started.

First I did not get the OS selection (Grub?) at startup. My computer just booted up in Win XP, as if nothing had changed. I fixed that using a guide from this forum. Now I get the selection screen, and Ubuntu works fine, but if I select Win XP, I get the following. Error 22: No such partition. If have tried pressing "e" on the selection menu on Win XP, and tried using all the different bootoptions, but nothing works.

I have posted a selection of info below, that might be usefull, for some of you wise people, to tell me what to do. If I should guess, I would say that I need to edit menu.lst, but I rather not break more than I allready have. 

**My fdisk -l results:**

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28004b99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48564855

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       41125   330336531    7  HPFS/NTFS
/dev/sdb2           41126       60801   158047470    5  Extended
/dev/sdb5           41126       59997   151589308+  83  Linux
/dev/sdb6           59998       60801     6458098+  82  Linux swap / Solaris


**Some of my menu.lst:**

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by Treepwood on 2009-10-19
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28004b99

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48564855

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   660,673,124   660,673,062   7 HPFS/NTFS
/dev/sdb2         660,673,125   976,768,064   316,094,940   5 Extended
/dev/sdb5         660,673,188   963,851,804   303,178,617  83 Linux
/dev/sdb6         963,851,868   976,768,064    12,916,197  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="98F8ED56F8ED32E4" TYPE="ntfs" 
/dev/sdb5: UUID="906e76b9-9d45-4c85-aa52-5e7a67b181de" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="22825d6d-9d88-4243-82e9-72e0e7820c12" 

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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=906e76b9-9d45-4c85-aa52-5e7a67b181de

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
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        906e76b9-9d45-4c85-aa52-5e7a67b181de
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
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
UUID=906e76b9-9d45-4c85-aa52-5e7a67b181de /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=22825d6d-9d88-4243-82e9-72e0e7820c12 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 343.4GB: boot/grub/menu.lst
 343.3GB: boot/grub/stage2
 343.3GB: boot/initrd.img-2.6.28-11-generic
 343.3GB: boot/initrd.img-2.6.28-15-generic
 343.4GB: boot/vmlinuz-2.6.28-11-generic
 343.4GB: boot/vmlinuz-2.6.28-15-generic
 343.3GB: initrd.img
 343.3GB: initrd.img.old
 343.4GB: vmlinuz
 343.4GB: vmlinuz.old

---

### Post by arrange on 2009-10-19
What's this empty 1TB disk for (*sda*)? How is the booting priority set in BIOS?

You could try using ```
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
makeactive
chainloader +1
```for the Win part of *menu.lst*.

---

### Post by Treepwood on 2009-10-19
I cant edit menu.lst. It says I dont have permission. Could not save the file /boot/grub/menu.lst

The other disk is just for future backup. It is not in the bootorder in bios.

---

### Post by bulldog on 2009-10-19
To edit the menu.lst
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by arrange on 2009-10-19
Don't change the menu.lst directly. Just press 'e' in the Grub menu at boot-up as you did before.

---

### Post by saif_held on 2009-10-19
you should run this task as admin. or sudo. 

Simply from the terminal type:

sudo <and the command you want to exectute>

---

### Post by Treepwood on 2009-10-19
Both disk have been there from before I installed Ubuntu. They are SATA. Before Ubuntu I had Win 7 on the 1TB disk, and XP on the 500GB disk. I deleted the partition on the Win 7 disk, planing to use that disk as storage and share the 500GB disk between XP and Ubuntu.

If I dont edit, what should I do? Can i break anything by trying the edit hint?

---

### Post by arrange on 2009-10-19
> **Treepwood said:**
> 
If I dont edit, what should I do? Can i break anything by trying the edit hint?

No, not at all. Have a look at [Herman's page]("http://members.iinet.net/~herman546/p15.html"), part *Temporarily Edit the GRUB Menu*.

---

### Post by Treepwood on 2009-10-19
I tried editing to this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    **(hd0,0)**
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1 	

Now I dont get the error, but it changes to a screen saying: Starting up.....  and nothing more happens.

---

### Post by Treepwood on 2009-10-19
Wuhuuu

I did as Arrange said and removed the two lines I did not remove in the first edit, and now it is working.

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
makeactive
chainloader +1
Thanks to all of you for your help.

---

