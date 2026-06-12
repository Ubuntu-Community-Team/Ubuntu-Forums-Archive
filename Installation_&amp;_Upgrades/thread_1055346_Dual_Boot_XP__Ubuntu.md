---
title: "Dual Boot XP / Ubuntu"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by buzov007 on 2009-01-30
I installed Xp first then Ubuntu,but when i get in grub,i choose xp and i get error NTLDR is missing.What now????



Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2549    2550-  20482843+   7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3       8454    9728    1275   10241437+   5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       8454+   9668    1215-   9759456   83  Linux
/dev/sda6       9669+   9728      60-    481918+  82  Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  38912   38913- 312568641    7  HPFS/NTFS
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

---

### Post by Rompalle on 2009-01-30
can you boot in Ubuntu and post the contents of your grub menu.lst ?

```
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2009-01-30
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And if your Windows is on sda1 (the same drive as Ubuntu) use the following entry:
```
title Windows XP
root (hd0,0)
chainloader +1
```
But if Windows is actually on your sdb drive, use the following instead:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try Windows from Grub, and let me know how far you get.

---

### Post by buzov007 on 2009-01-30
here are the result from cat /boot/grub/menu.lst 
what to do now?

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
# kopt=root=UUID=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e06bf2cf-40ee-4ae8-9bb1-2a98d5892b66
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by buzov007 on 2009-01-30
What now??

---

### Post by Rompalle on 2009-01-30
> **buzov007 said:**
> What now??

your grub seems to be good as far as i know. Looked at your original message again it it looks like you have 2 ntfs partitions, one on each disk ? Grub might be booting the wrong one.

lets see with this command, it will list all mounted filesystems and partitions.
 
```
 sudo fdisk -l
```

---

