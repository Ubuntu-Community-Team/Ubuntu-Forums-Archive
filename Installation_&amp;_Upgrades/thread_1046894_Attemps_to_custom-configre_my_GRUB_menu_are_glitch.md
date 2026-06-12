---
title: "Attemps to custom-configre my GRUB menu are glitchy"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2009-01-21
Since I have several operating systems I boot from, I tried to custom-configure my GRUB menu.

I wanted to seperate each series of Operating Systems into their own section, but I wound up with two problems:

1. The menu options scroll off the box and off the screen, is there any way to make GRUB display in a type of "full screen" mode instead of limiting the boot options to the little box it uses?

2. The menu options are invisible... until I highlight that option it appears blank, and once its scrolled off the box it becomes invisible again unless I highlight that option again.

Heres what my menu.lst looks like:

[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

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
# kopt=root=UUID=f2e0ec88-025b-4700-816d-dc01c8ec8d17 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f2e0ec88-025b-4700-816d-dc01c8ec8d17

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

title		GRUB Boot Manager
root

title		
root

title		------------------------------------------
root

title		Microsoft Windows:
root

title		---
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		------------------------------------------
root


title		
root

title		------------------------------------------
root


title		Ubuntu Linux:
root

title		---
root



title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f2e0ec88-025b-4700-816d-dc01c8ec8d17
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2e0ec88-025b-4700-816d-dc01c8ec8d17 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2e0ec88-025b-4700-816d-dc01c8ec8d17
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2e0ec88-025b-4700-816d-dc01c8ec8d17 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		------------------------------------------
root

title		
root

title		------------------------------------------
root

title		OpenSUSE Linux:
root

title		---
root

###Orignally added by: YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-WDC_WD5000BEVT-00ZAT0_WD-WXNY08SA7653-part6 resume=/dev/disk/by-id/ata-WDC_WD5000BEVT-00ZAT0_WD-WXNY08SA7653-part8 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default

###Orignally added by: YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-WDC_WD5000BEVT-00ZAT0_WD-WXNY08SA7653-part6 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.27.7-9-default



title		------------------------------------------
root

title		
root


title		------------------------------------------
root

title		Apple MacOS:
root

title		---
root


title		MacOSX 10.5.2
root (hd0,2)
chainloader +1

title		------------------------------------------
root


title		
root


title		------------------------------------------
root

title		Utilities:
root

title		---
root


title		Ubuntu 8.10, memtest86+
uuid		f2e0ec88-025b-4700-816d-dc01c8ec8d17
kernel		/boot/memtest86+.bin
quiet

title		------------------------------------------
root

[/HTML]

---

### Post by Shazaam on 2009-01-21
Get rid of this in the middle...
```
title		
root

```
listed by itself in several places in your menu.lst
You may also be able to change the resolution of the grub boot screen using Startup-Manager. Get it through Synaptic.

---

### Post by Cyber Akuma on 2009-01-21
> **Shazaam said:**
> Get rid of this in the middle...
```
title		
root

```
listed by itself in several places in your menu.lst
You may also be able to change the resolution of the grub boot screen using Startup-Manager. Get it through Synaptic.

Hmm, I was suspecting that.

What would be a good way to add a blank line then?

---

