---
title: "[SOLVED] moving a hdd from USB boot to internal"
date: 2008-08-29
forum: Hardware
---

### Post by moody_mark on 2008-08-29
I have a Dell Latitude D610 Laptop which has windows XP installed and all runs ok. I recently installed Kubuntu onto an old 15GB HDD i had salvaged from an old laptop and put that into one of those USB enclosures you get.

I wanted to try out ubuntu for my everyday work so Ive been booting from the USB drive and for the last week or so ive been running ubuntu instead of windows. Im very happy with it, and apart from some expected teething and setting up, even though its running from the USB it seems more responsive, faster to boot and load apps and easier to use.

So I have two questions;

1. If I take the ubuntu drive and swap it into my laptop to make it the internal drive, would I expect the performance of ubuntu to increase since its now running on an internal HDD?

2. If I do this will ubuntu boot ok? Will it find the disc ok as I thought that on boot up the device might be in a different location to where it thought it should be and cause a boot error

I wanted to ask before I tried it out in case it corrupted something on the file system somewhere - thanks

(if only some of my works internal websites didnt demand IE then I could install ubuntu onto my current internal drive which is bigger)

---

### Post by arch0njw on 2008-08-29
1) Yes.  USB is measurably slower than an internal drive speed (be that PATA or SATA).

2) The drive will be at a different device mount.  So right now you will find that your internal drive is something like /dev/sda and all the partitions on it are sda1, sda2, sda3, etc.  Your USB drive you'll find is something like /dev/sdb with similar partitions.  There is also the matter of the drive being bootable.  You probably have GRUB controlling your boot installed on your internal drive -- the USB drive is probably not going to boot.

---

### Post by falcon61102 on 2008-08-29
Well, I don't know the rest of the specs on your laptop but you may be better off going with a dual boot setup.  That way you can have XP and Ubuntu on the same HD and can switch between them any time you restart.  I'm guessing that you have a larger HD currently installed in your laptop and keeping that installed would probably be better for you.

---

### Post by moody_mark on 2008-08-29
Yes, my USB drive is /dev/sdb1 and the laptop drive has two paritions which are /dev/sda1 and /dev/sda5

Also my fstab file shows the following 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90640b00-30b0-4340-9444-c2dc60ca542c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a139cc6f-7971-4602-8d7b-ecfd77afd7f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Is this the best place to find out whats mounted where? Can i edit this file to change what drive boots up?

---

### Post by falcon61102 on 2008-08-29
What is the contents of your menu.lst?  It can be found in /boot/grub.

---

### Post by moody_mark on 2008-08-29
The contents on the menu.lst file is as follows

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
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=90640b00-30b0-4340-9444-c2dc60ca542c ro

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=90640b00-30b0-4340-9444-c2dc60ca542c ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=90640b00-30b0-4340-9444-c2dc60ca542c ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by falcon61102 on 2008-08-29
If you were to install that HD into your laptop, the only problem you may have is that the UUID for the HD may change and need to be updated in your menu.lst.  Other than that, it should boot right up.  You can see where I'm talking about if you look at the very end of the file, you will see the listtings for the Ubuntu Kernals and in the third line of each, you will see where it has the UUID written

---

### Post by moody_mark on 2008-08-29
> **falcon61102 said:**
> You can see where I'm talking about if you look at the very end of the file, you will see the listings for the Ubuntu Kernals and in the third line of each, you will see where it has the UUID written

Ah yes thank you, i see, so it will always boot from HD0,0? If that ID does change is there anyway of finding out what its changed to?

---

### Post by falcon61102 on 2008-08-29
HD0,0 mean the first partition of the first drive so installing it into your laptop will not change that value.  You will still be booting from the first partition of the first drive.  The only value that may change is that UUID.  If it changes, boot up with the LiveCD and you can check it there.  It shouldn't give you any trouble though.

---

### Post by moody_mark on 2008-08-29
Thanks a lot for your help. I booted ok without having to change any settings. Strangely enough the windows HDD now in the usb caddy , will not boot. I suspect that it needs a boot loader on there, or a change to my current boot loader but not to worry. I dont intend on using the Windows environment unless its absolutely necessary.

:-)

---

