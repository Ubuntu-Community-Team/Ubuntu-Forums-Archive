---
title: "can't enter on my ubuntu..grub problem"
date: 2008-07-16
forum: General Help
---

### Post by xdavidx on 2008-07-16
when i start my computer he makes a auto run if i don't press esc, and when i press it the only boot options i have are the memtest all the others have gone.. see the menu.lst and help me please.


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
# kopt=root=UUID=715bf5ed-50c8-4726-9a4e-d241091e171e ro

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
# defoptions=splash locale=pt_PT

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

title		Ubuntu 8.04, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
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
# kopt=root=UUID=715bf5ed-50c8-4726-9a4e-d241091e171e ro

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
# defoptions=splash locale=pt_PT

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

title		Ubuntu 8.04, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
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
# kopt=root=UUID=715bf5ed-50c8-4726-9a4e-d241091e171e ro root=UUID=715bf5ed-50c8-4726-9a4e-d241091e171e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0 0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0) (hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash locale=pt_PT splash locale=pt_PT

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0 console=tty0

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
# howmany=all all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false false

## ## End Default Options ##

title		Ubuntu 8.04, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 8.04, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by chicken101 on 2008-07-16
OK, well I personally think the easiest way to resolve these types of issues are to reconfigure the grub menu with the supergrub cd which can be found [here]("http://www.supergrubdisk.org/").

This will really save you a ton of trouble, I've been in situations when my GRUB menu simply refuses to work right, and this bootable tool will save you a lot of time.:KS

---

### Post by Elfy on 2008-07-16
> **chicken101 said:**
> OK, well I personally think the easiest way to resolve these types of issues are to reconfigure the grub menu with the supergrub cd which can be found [here]("http://www.supergrubdisk.org/").

This will really save you a ton of trouble, I've been in situations when my GRUB menu simply refuses to work right, and this bootable tool will save you a lot of time.:KS

+1

While you're getting that and burning it get a copy of [partedmagic]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads") and you should be set up for most problems with your livecd as well.

Both need to be burnt as isos so that they are bootable.

You can alos use the livecd if you can't get online

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tyler_roach on 2008-07-16
To see the grub menu at boot time, comment out the line "hiddenmenu" so it reads:

#hiddenmenu

Also, it would be a good idea to edit the line above it to read:
timeout 10 

To boot into Ubuntu, add the following lines to your menu.lst file:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

However, you may need to make the following changes:
If you are using an ATA hard drive, you may need to have "root=/dev/hda1" instead of sda1.
If you didn't do the most recent updates, your kernel version may be different, and you may have to change the last line (the "initrd... " one) on each section. If you can mount your drive from a liveCD, look in the /boot directory and find the most recent kernel, and modify your menu.lst accordingly.

Super Grub Disk will _not_ work for you, it can only restore grub to the MBR, but it does not modify the menu.lst file, where your problem is.

---

### Post by Elfy on 2008-07-17
See if you have any backups first

```
ls /boot/grub/menu.*
```

Possibel to update grub with

```
sudo update-grub
```

---

### Post by xdavidx on 2008-07-17
> **tyler_roach said:**
> To see the grub menu at boot time, comment out the line "hiddenmenu" so it reads:

#hiddenmenu

Also, it would be a good idea to edit the line above it to read:
timeout 10 

To boot into Ubuntu, add the following lines to your menu.lst file:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

However, you may need to make the following changes:
If you are using an ATA hard drive, you may need to have "root=/dev/hda1" instead of sda1.
If you didn't do the most recent updates, your kernel version may be different, and you may have to change the last line (the "initrd... " one) on each section. If you can mount your drive from a liveCD, look in the /boot directory and find the most recent kernel, and modify your menu.lst accordingly.

Super Grub Disk will _not_ work for you, it can only restore grub to the MBR, but it does not modify the menu.lst file, where your problem is.

i can mount it through live cd but i can't modify it cause it asks for root privileges..if i could do it i would change it for a backup that i have..

---

### Post by xdavidx on 2008-07-17
> **forestpixie said:**
> See if you have any backups first

```
ls /boot/grub/menu.*
```

Possibel to update grub with

```
sudo update-grub
```

i'll try that, thks.

---

### Post by Elfy on 2008-07-17
Re-read, you can't update grub - it won't get to a root prompt.]

You should be able to check whether you have any backups in the livecd.

You cna open nautilus as root and then navigate to the real menu.lst and open it you should have rights then.

```
gksudo nautilus
```

---

