---
title: "Kernel Panic while booting (Not syncing: VFS, hda0,0)"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by SargoDarya on 2009-04-23
I got a problem after installing Jackalope 9.04 when trying to boot the realtime kernel. The exact error message:

"Kernel Panic - not syncing: VFS Unable to mount root fs on unknown block (0,0)"

No problems when using the generic kernel but the rt kernel won't boot. Here's my menu.lst:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=107d17b7-7eae-48f4-ad59-363d7aa5af07 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=107d17b7-7eae-48f4-ad59-363d7aa5af07

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		107d17b7-7eae-48f4-ad59-363d7aa5af07
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=107d17b7-7eae-48f4-ad59-363d7aa5af07 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		107d17b7-7eae-48f4-ad59-363d7aa5af07
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=107d17b7-7eae-48f4-ad59-363d7aa5af07 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-3-rt
uuid		107d17b7-7eae-48f4-ad59-363d7aa5af07
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=107d17b7-7eae-48f4-ad59-363d7aa5af07 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-rt
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-3-rt (recovery mode)
uuid		107d17b7-7eae-48f4-ad59-363d7aa5af07
kernel		/boot/vmlinuz-2.6.28-3-rt root=UUID=107d17b7-7eae-48f4-ad59-363d7aa5af07 ro  single

title		Ubuntu jaunty (development branch), memtest86+
uuid		107d17b7-7eae-48f4-ad59-363d7aa5af07
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows Vista (loader)
#rootnoverify	(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


```

Hope someone can help me on this issue. Thanks in advance.

Sargo

---

### Post by s.dalas on 2009-04-23
install aq GrubEditor.
Enter the properties of generic kernel which is working
There you will see something like hd(0,0).

Put this setting to the other kernels and will load.

---

### Post by jchavezb on 2009-04-27
Experiencing the same issue after the last update to 9.04 which I had installed originally as RC1 on a Breeze 3110 from ZaReason.

I will try to fix but what would be the root cause for this?

---

