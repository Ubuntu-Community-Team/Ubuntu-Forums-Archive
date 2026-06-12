---
title: "Upgrade to 9.10 humped Grub"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Gorf on 2009-11-06
Greetings all, I have spent the day trying to follow the many posts out there regarding how to fix my Error: 15 problem with Grub post-upgrade to 9.10.  I'm forced now to work off of my live CD.

My system is just a vanilla filesystem layout:

/dev/sda1 - /boot
/dev/sda2 - extended partition
/dev/sda5 - swap
/dev/sda6 - /

/dev/sda1 is marked as Boot in the flags.  

Currently my menu.lst works like this:

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=5c7d6f5e-e41f-4094-a92e-d29ca40b1f6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4a9b61d8-ea05-4eab-8737-22b56e42ac47

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		4a9b61d8-ea05-4eab-8737-22b56e42ac47
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=5c7d6f5e-e41f-4094-a92e-d29ca40b1f6c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		4a9b61d8-ea05-4eab-8737-22b56e42ac47
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=5c7d6f5e-e41f-4094-a92e-d29ca40b1f6c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		4a9b61d8-ea05-4eab-8737-22b56e42ac47
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=5c7d6f5e-e41f-4094-a92e-d29ca40b1f6c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		4a9b61d8-ea05-4eab-8737-22b56e42ac47
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=5c7d6f5e-e41f-4094-a92e-d29ca40b1f6c ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		4a9b61d8-ea05-4eab-8737-22b56e42ac47
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

booting from the alternative CD and doing all sorts of grub-probe, grub-install, etc has so far had no effect.  It seems like /dev/sda1 has lost it's UUID or something. It's UUID  4a9b61d8-ea05-4eab-8737-22b56e42ac47 that it complains it can't find yet I can clearly see that UUID via tun2fs -l /dev/sda1.

Any thoughts?  I have a ton of data on this system and I really don't want to have to do a clean install if I can help it.

---

### Post by Gorf on 2009-11-06
So I don't know if this helps or not, but from within the Grub command prompt if I issue:

find /boot/grub/stag2

I get the Error 15: file not found.

So does that mean that stage2 is humped?  I have no idea how to repair this.

---

### Post by wojox on 2009-11-06
This may help [“Error 15: File not found!”]("http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/")

---

