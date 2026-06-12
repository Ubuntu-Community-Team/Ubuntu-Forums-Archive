---
title: "GRUB doesn't work anymore."
date: 2008-07-16
forum: General Help
---

### Post by Newuser1111 on 2008-07-16
After installing another OS and trying to reinstall GRUB everything on it just says:
> Error 17: Cannot mount selected partition

Press any key to continue...


I used post #5 on [http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by danwood76 on 2008-07-16
What other OS were you trying to install?

Can you post the output of your menu.lst and your fdisk list?

Within a ubuntu Live CD do:
```

sudo fdisk -l

```
You also need to mount your boot partition and dump the menu.lst from within it.

---

### Post by Newuser1111 on 2008-07-16
> **danwood76 said:**
> What other OS were you trying to install?OS X, because it broke so I was reinstalling it.

> Can you post the output of your menu.lst and your fdisk list?```

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
# kopt=root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

#title		Ubuntu 8.04.1, kernel 2.6.24-19-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-386
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-19-386

#title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-virtual
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-virtual (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-19-virtual

#title		Ubuntu 8.04.1, kernel 2.6.24-19-server
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-server
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-19-server

#title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-19-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-openvz
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-19-openvz

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-18-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-386
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-386

#title		Ubuntu 8.04.1, kernel 2.6.24-18-virtual
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-virtual
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-virtual (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-virtual

#title		Ubuntu 8.04.1, kernel 2.6.24-18-server
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-server
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-server (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-server

#title		Ubuntu 8.04.1, kernel 2.6.24-18-rt
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-18-openvz
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-openvz
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-openvz (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-openvz

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-18-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-386
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-386

#title		Ubuntu 8.04.1, kernel 2.6.24-16-virtual
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-virtual
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-virtual (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-virtual root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-virtual

#title		Ubuntu 8.04.1, kernel 2.6.24-16-server
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-server
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-server (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-server

#title		Ubuntu 8.04.1, kernel 2.6.24-16-rt
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-rt
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-rt (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-rt

#title		Ubuntu 8.04.1, kernel 2.6.24-16-openvz
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-openvz
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-openvz (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-openvz root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-openvz

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=568a959e-9df2-4af9-a85a-c0b942023ccd ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=568a959e-9df2-4af9-a85a-c0b942023ccd ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot



```


> Within a ubuntu Live CD do:
```

sudo fdisk -l

```
You also need to mount your boot partition and dump the menu.lst from within it.```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a695

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36042   289499960    7  HPFS/NTFS
/dev/sdb2           36043       37347    10482412+  af  Unknown
/dev/sdb3           37349       37607     2080417+  82  Linux swap / Solaris
/dev/sdb4   *       37608       38913    10490445   83  Linux
ubuntu@ubuntu:~$
```

---

### Post by danwood76 on 2008-07-16
You need to edit your menu.lst file and change a few things.
Personally I would clean it up to start with.

Basically your Ubuntu is looking at the wrong drive to boot from.
It should be hd0,3 not hd0,2

Below is what I think your menu.lst should look like.

```

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
# kopt=root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0ac4807f-4d27-4db0-a1a3-4df2fe623e35 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu, memtest86+ (on /dev/sdb4)
root		(hd0,3)
kernel		/boot/memtest86+.bin  
savedefault
boot

```
I have removed all the commented kernel entries and ones that dont apply to hardy.
You probably want to add chainloader lines to boot your OSX and XP partitions.

-- edit --

Forgot to say that this relies on the UUID's not changing since you messed the partitions about.
You can verify this from the live CD by running:
```

sudo blkid

```
ANd checking the UUID's with your menu.lst

---

