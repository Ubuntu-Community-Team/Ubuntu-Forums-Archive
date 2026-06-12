---
title: "Does the Grub list for default boot value include the seperator?"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-10-24
Basically, I commented (#) all the boots I didn't want included in Grub, to leave only three:

Ubuntu, Ubuntu recovery mode and Vista

However when I set the default value to 2, the highlighted value isn't Vista, it's the seperator between the two (Linux vs Windows)

What I'm wondering is, should I set the default to 3, or should I leave it this way and Vista would boot automatically anyway..?

Thanks!

---

### Post by mikewhatever on 2009-10-24
Post your menu.lst for review.

tail -n 30 /boot/grub/menu.lst

---

### Post by phillw on 2009-10-24
Hi,

do you want the default boot to be ubuntu or windows ?

Phill.

---

### Post by Pott on 2009-10-24
I'd like the default to be Vista.

I'm not on Ubuntu right now... will post it when I boot back on it :)

---

### Post by Pott on 2009-10-24
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
default        2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        7

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
# kopt=root=UUID=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        d25e3a19-8bfb-4a53-84f0-74eecf7b01d9
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9 ro quiet splash acpi_backlight=vendor
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        d25e3a19-8bfb-4a53-84f0-74eecf7b01d9
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        d25e3a19-8bfb-4a53-84f0-74eecf7b01d9
#kernel        /boot/vmlinuz-2.6.28-11-generic #root=UUID=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        d25e3a19-8bfb-4a53-84f0-74eecf7b01d9
#kernel        /boot/vmlinuz-2.6.28-11-generic #root=UUID=d25e3a19-8bfb-4a53-84f0-74eecf7b01d9 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        d25e3a19-8bfb-4a53-84f0-74eecf7b01d9
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Windows Vista (loader)
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title        Microsoft Windows XP Embedded
#rootnoverify    (hd0,3)
#savedefault
#makeactive
#chainloader    +1


is my current grub file

---

### Post by mikewhatever on 2009-10-24
Number 3 should boot Windows, just go ahead and change it.

---

### Post by Pott on 2009-10-24
It won't mess anything up if the value is wrong? I mean if three doesn't work and none are selected by default, will it still all work ok?

---

### Post by Mark Phelps on 2009-10-26
To answer your oiginal question, YES, GRUB counts the separator.

And no, it doesn't hurt anything the experiment with the default number. All that will happen is that it will not boot into what you want.

Just reboot into something that works, change the default number, and reboot again.

---

