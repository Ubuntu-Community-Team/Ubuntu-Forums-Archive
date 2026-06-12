---
title: "Grub won't boot default entry"
date: 2008-08-20
forum: General Help
---

### Post by bluesky74656 on 2008-08-20
For a while now I've had the RT kernel installed alongside the generic kernel, and I would have to manually select the generic kernel in grub when I needed it.  

I finally decided to change the default boot option in Grub by editing /boot/grub/menu.lst, and changing default from 0 to 2, which should be the generic kernel.  When I rebooted, the generic kernel was highlighted, but after waiting for the timeout the system hung at "Starting Up" after the grub menu.  If I hit enter on the default highlighted entry it starts without a problem.

In my desperation, I uninstalled the RT kernel, then reinstalled Grub, all to no success.  I also tried changing the commented lines under Default Options 'updatedefaultentry' and 'savedefault'.  In addition, I tried the command grub-set-default and update-grub.  Please, if you can, help me get this system to boot into Ubuntu without user intervention.

My menu.lst is pasted below for reference.

```

####   menu.lst    ####
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.24-18-rt

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=12278813-02f0-4181-8013-a41e6cd1b3de ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by spiderbatdad on 2008-08-20
Your menu list shows generic=0 RT=2. What are you trying to do? What is the problem...system hangs booting the generic kernel?

---

### Post by bluesky74656 on 2008-08-20
Right... after my first failed attempt, I just removed the RT kernel and it's current entries altogether, and changed the default back to 0.  That didn't help the problem.

I'm trying to boot the generic kernel without user intervention.  If I wait for the timeout countdown, the system hangs at the next screen, which just says "Starting Up".  I'm not sure if that's grub or the kernel.  However, if I hit enter on the same entry before the timeout, the system boots normally.  I want the system to boot normally without my doing anything.

---

### Post by spiderbatdad on 2008-08-20
I can't find anything wrong. What's with the crashdump option after kopt...I don't have that in menu.lst? Everything else look like it should work. You have a second disk for ubuntu and have groot pointing to it...

maybe a bios setting needed to allow booting to second disk without user intervention.

---

### Post by bluesky74656 on 2008-08-21
Okay, added difficulty, then.  It worked properly before I started mucking with menu.lst.

By that, I mean that before I changed anything, if I left it alone, it would boot into the RT kernel with no qualms.  It only started doing this after I removed the RT Kernel and/or changed the default.  That would seem to suggest that it's not a BIOS problem.


Here's a somewhat related question.  If I tell Synaptic to reinstall Grub, does it completely reinstall and rebuild everything, including the .lst file?  Because I tried reinstalling Grub, and it didn't help.

---

