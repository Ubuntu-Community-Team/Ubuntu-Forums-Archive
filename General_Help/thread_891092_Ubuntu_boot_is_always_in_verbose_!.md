---
title: "Ubuntu boot is always in verbose !"
date: 2008-08-15
forum: General Help
---

### Post by Scypher on 2008-08-15
My Ubuntu boot sequence is stuck in verbose mode currently, I once wanted to see the potential error messages but now that my system is perfectly stable I don't see the point of having to see these lines of text anymore. Can anyone help me getting rid of the awful verbose mode ? I tried everything I knew... <_<

Each time I boot, I see the splash theme during 5-8 seconds and after that my screen goes right the the verbose mode.... <_<

Here is à copy of my: /boot/grub/menu.lst


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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=c877ea0c-5395-4204-ab50-3c618d6ef611 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=splash vga=789 quiet rootflags=data=writeback

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
# altoptions=(recovery mode) single rootflags=data=writeback

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c877ea0c-5395-4204-ab50-3c618d6ef611 ro splash vga=789 quiet rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c877ea0c-5395-4204-ab50-3c618d6ef611 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I hope this help. Thanks to those willing to help me and sorry for my bad grammar and English syntax.

---

### Post by coffeecat on 2008-08-15
Have you reformatted or resized your swap partition recently? Or installed another distro on another partition? No, I haven't gone barmy and, yes, I did read your post. The symptoms you describe are the result of a commonly-encountered bug. It's all to do with initramfs having the wrong UUID for the swap partition. See my first post (post #5) in [this thread]("http://ubuntuforums.org/showthread.php?t=857565").

If this is the cause of your problem, I've posted the fix there and also some useful links.

---

### Post by sdennie on 2008-08-15
Try adding "splash" as an option for defoptions then run:

```

update-grub

```

Edit:
Nevermind.  I just noticed that "splash" is already there.  I must have been fixated on seeing it with "quiet" and not noticed.  ;)

---

### Post by bodhi.zazen on 2008-08-15
Just a few guesses ....

1. vga=789 is probably not needed. Try removing it from your kernel options.

2. Are you getting any error messages as you are booting ?

---

### Post by Scypher on 2008-08-15
No error messages :P

My install seems perfect.

I didnt try to mess with my swap or install any other OS on my hard drive.

---

### Post by Scypher on 2008-08-15
WOW IT WORKS !

But now there is another problem...

My progress bar doesn't seems quite useful as it doesn't progress like it should.

My computer always shutdown, or boot before the progress bar reaches it's end.

---

