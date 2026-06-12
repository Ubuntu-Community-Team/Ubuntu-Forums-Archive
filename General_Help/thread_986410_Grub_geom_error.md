---
title: "Grub geom error"
date: 2008-11-18
forum: General Help
---

### Post by Grandy on 2008-11-18
Hi

im new to linux and ive' just installed ubuntu 8.04

the problem is that when i try to start upp the system it says "grub geom error" :(

---

### Post by Glubbdubdribian on 2008-11-18
[http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error](http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error)

Google is your friend :D

---

### Post by caljohnsmith on 2008-11-18
How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
Also, try reinstalling Grub to the MBR (Master Boot Record) of you HDD via these steps:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know if anything changes. We can work from there if you want.

---

### Post by Grandy on 2008-11-18
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x205248ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09070906

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160826714    80413326    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7edf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     6297479     3148708+   7  HPFS/NTFS
/dev/sdc2         6297480   586099394   289900957+   5  Extended
/dev/sdc5         6297543    46363589    20033023+  83  Linux
/dev/sdc6       583079238   586099394     1510078+  82  Linux swap / Solaris
/dev/sdc7        46363653   580058954   266847651   83  Linux
/dev/sdc8       580059018   583079174     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   398283479   199141708+   7  HPFS/NTFS

Disk /dev/sde: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6972706d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63    49200479    24600208+  83  Linux
/dev/sde2   *    51196320   625008751   286906216    7  HPFS/NTFS
/dev/sde3        49200480    51196319      997920   82  Linux swap / Solaris

Partition table entries are not in disk order



-----

grub> find /boot/grub/stagel

Error 15: File not found

grub> find /grub/stagel

Error 15: File not found


------

is this too any help ?

---

### Post by Grandy on 2008-11-18
or this, (menu.lst)

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
# kopt=root=UUID=d8d46129-cf36-4c60-b61f-a68865ecce6b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd4,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d8d46129-cf36-4c60-b61f-a68865ecce6b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd4,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d8d46129-cf36-4c60-b61f-a68865ecce6b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd4,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdc5)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0425724a-92d2-466d-abe6-d8a5031ca1a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdc5)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0425724a-92d2-466d-abe6-d8a5031ca1a6 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title		Ubuntu 8.10, memtest86+ (on /dev/sdc5)
root		(hd2,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde2
title		Microsoft Windows XP Professional
root		(hd4,1)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1

---

### Post by caljohnsmith on 2008-11-18
So which partition and drive is Ubuntu on? Also, use a number 1 in the Grub commands you ran, not a lowercase L:
```
grub> find /boot/grub/stage[COLOR="Red"]1[/COLOR]
grub> find /grub/stage[COLOR="Red"]1[/COLOR]
```

---

### Post by Grandy on 2008-11-18
> **caljohnsmith said:**
> So which partition and drive is Ubuntu on? Also, use a number 1 in the Grub commands you ran, not a lowercase L:
```
grub> find /boot/grub/stage[COLOR="Red"]1[/COLOR]
grub> find /grub/stage[COLOR="Red"]1[/COLOR]
```


grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

=S

---

