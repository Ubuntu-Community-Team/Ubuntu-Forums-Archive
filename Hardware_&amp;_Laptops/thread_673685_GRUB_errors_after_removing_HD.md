---
title: "GRUB errors after removing HD"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by DaveDel on 2008-01-20
I successfully installed and ran Ubuntu 7.10 for a week, dual boot with Losedoz 2k, but tried to remove an unused hard drive and started getting Grub error 21 or 17. Putting the hd back in, everything is fine again.

How do I tell Grub about the "missing" hd?

---

### Post by erfahren on 2008-01-20
post the output of 
```

cat /boot/grub/menu.lst

```

---

### Post by DaveDel on 2008-01-20
HD2 is the drive I want to remove...

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
# kopt=root=UUID=c3d0e27e-4beb-424f-9a42-a3a9772eccaf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3d0e27e-4beb-424f-9a42-a3a9772eccaf ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3d0e27e-4beb-424f-9a42-a3a9772eccaf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows 2000 Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by erfahren on 2008-01-21
I take it that the drive you're trying to take out is the one that's listed as (hd2,0) with Win2K at the bottom, is it? 

you'd need to remove the entries out of your /etc/fstab as well, BUT, if it is that second drive it would change where GRUB is located (the # groot=(hd3,0) part) - basically the drive mapping will be different.

to be honest at this point this is beyond my expertise - but I can tell what I do know which may help

removing the entries for the drive out of your /etc/fstab should be less of a problem since it now uses [UUID (Universally Unique Identifier)](http://linux.byexamples.com/archives/321/fstab-with-uuid/) 

then you'd have to reconfigure GRUB to find where the Ubuntu root is located (basically - GRUB just installs it's IPL (Initial Program Loader) to the Master Boot Record which points it to where GRUB itself is actually located - there's information on how to do that on hermanzone's GRUB page:
(also look at the section on Editing GRUB's device.map):
[http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

I hope that'll get you going a little more

---

### Post by DaveDel on 2008-01-21
Greatly appreciate it, Erfahren.... I spent a summer in Germany, and the most thrilling experience -- even better than LINUX! -- is fahren 250 kph on the autobahn in a borrowed Mercedes. Now I'm stuck with my '74 Superbeetle on New York interstates. :)

---

