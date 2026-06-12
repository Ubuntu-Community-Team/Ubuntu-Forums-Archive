---
title: "Hardy Realtime kernel"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by pedrocortez on 2009-10-15
Hi 

I am trying to install realtime kernel in Hardy 8.04. 
I already have a seperate partition with Ubuntu Studio with -rt kernel and want to upgrade the Hardy partition to have it also. 

Ive installed rt kernel and headers using terminal and have checked that they are there in synaptic, but then no realtime kernel option shows in my grub boot menu. 

when i do  *uname - r  *i just get the generic 2.6.24.24 Hardy kernel showing. 

Ive added an "audio" group and edited my limits.conf file too. 

What do I need to do ? 

cheers
Pete

---

### Post by s.dalas on 2009-10-15
the command uname -r shows the kernel that is in use "by default".

post here the output of the command ```
sudo gedit /boot/grub/menu.lst
```

here you will see if the kernel is installed and you will change the order.
post it here and we will see

---

### Post by pedrocortez on 2009-10-15
thanks 

heres the output

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
# kopt=root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-rt
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-rt root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-rt
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-rt (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-rt root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro single
initrd        /boot/initrd.img-2.6.24-24-rt

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=83a4c8ad-7ee4-4fc6-87e1-040581dccd44 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

hope thts ueful

I see the options for my Ubuntu Studio rt kernel installation ( the first 2 options in grub list ) but no rt for the main Hardy partition ( all the other after the first 2 ) ? 

Rgds
Pete

---

### Post by s.dalas on 2009-10-15
ok so where is your Hardy partition??
i only see two partitions (two OS). your ubuntu partition is the same with rt and generic kernels

---

### Post by pedrocortez on 2009-10-15
Hi again 

well....

I installed both Hardy and then Ubuntu Studio onto separate partitions, and still have XP ( which I dont use anymore ! ) 

When i boot into the rt kernel i get Ubuntu studio desktop installation 
when i boot into the generic kernel I get the standard Hardy partition installation - at least that's what desktop comes up each way - and I thought they were separate partition installations. 
I have totally seperate apps on each !

any ideas ? 

Rgds
Pete

---

### Post by s.dalas on 2009-10-15
well the partitions on grub shows as (hd 0,1), (hd 0,0), (hd a,b)
i see that you have only 2. let me make a search for this and also w8 for someone with more experience that might see this and try to help

---

