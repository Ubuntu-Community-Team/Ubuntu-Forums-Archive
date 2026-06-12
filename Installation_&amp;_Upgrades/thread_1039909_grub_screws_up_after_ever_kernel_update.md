---
title: "grub screws up after ever kernel update"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2009-01-15
Everytime I update a kernel I have to manually edit menu.lst. It is getting a little annoying. /boot/grub/stage1 is on (hd0,0) but every time I update the menu.lst file gets edited for every ubuntu entry to (hd2,0). I fix it manually each time but what is the long term fix for this? I know it must be something as simple as reinstalling grub (maybe to hd2,0) but I don't recall the exact steps involved. Anyone able to help out?

---

### Post by iaculallad on 2009-01-15
Do you mean you had to have a "fixed" booting kernel? If that's the case, you should edit your menu.lst file and change the values of **updatedefaultentry** option.

Open the file for editing:

```
gksudo gedit /boot/grub/menu.lst 
```

Search for the entry below and make the changes.

> # updatedefaultentry=false

and change it to:


> # updatedefaultentry=true

Save and Close the file.

---

### Post by Skeorx13 on 2009-01-15
here is a copy of my menu.lst
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
# kopt=root=UUID=d87a4a93-95d0-4165-a876-dd1093687c4f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d87a4a93-95d0-4165-a876-dd1093687c4f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d87a4a93-95d0-4165-a876-dd1093687c4f ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d87a4a93-95d0-4165-a876-dd1093687c4f ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d87a4a93-95d0-4165-a876-dd1093687c4f ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

My problem is where for each ubuntu kernel it shows root as (hd0,0) but after installing the latest kernel the update changes my menu.lst file to read each entry of (hd0,0) to (hd2,0) so that none of them will boot until I edit the entries back to (hd0,0). The default kernel is always the newest kernel. This never changed on me and I would like to keep it that way. The entry for windows hasn't messed up ever.

---

### Post by iaculallad on 2009-01-15
Uncomment the line of text by deleting the # sign.

> # updatedefaultentry=true

to

> updatedefaultentry=true

and save.

---

### Post by caljohnsmith on 2009-01-15
Just change the groot line to use (hd0,0) instead of (hd2,0):
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
And then you should be all set.

---

