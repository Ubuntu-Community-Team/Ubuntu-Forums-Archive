---
title: "ACPI error AND keyboard?"
date: 2008-09-03
forum: General Help
---

### Post by Depressed Man on 2008-09-03
For the first problem (ACPI).

Occasionally when I boot up on my laptop, after selecting Ubuntu in Grub it will display something about an ACPI error. The only way to boot into Ubuntu is to then hard shutdown the computer (unplug the power cord) and rechoose Ubuntu. Annoying error (minor issue) but any help resolving this?

Also I've been using a keyboard (thru a PS/2 to USB converter so I can plug it into my laptop). It doesn't seem to recognize my keyboard correctly though. For example if I turn the numlock on. But press 2 on it, it opens up a terminal. Any idea why?

---

### Post by porchrat on 2008-09-03
Terminal from numpad thing...I have no clue.

However you can stop ubuntu booting with acpi by editing your grub menu.lst

please post the ouput of this here in this thread:

```
cat /boot/grub/menu.lst
```

---

### Post by Depressed Man on 2008-09-03
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
timeout		30

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
# kopt=root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader) [Recovery]
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader) [Vista]
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by porchrat on 2008-09-04
before you edit the grub menu i suggest you make a backup:
```
sudo mkdir /boot/grub/backup
sudo cp /boot/grub/menu.lst /boot/grub/backup/menu.lst.bak
```

This way if your menu.lst becomes corrupted when you edit it you can always reload the backup by booting from a liveCD.

now use gedit:
```
sudo gedit /boot/grub/menu.lst
```

and add "noacpi" to the end of the line containing kernel:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

```

that way it will look like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=94aa9b14-ec19-4d1f-9710-9309dae0c435 ro quiet splash noacpi
initrd		/boot/initrd.img-2.6.24-19-generic

```

This will stop ubuntu using acpi when it boots and hopefully solve your problem.  Please note though that it will cause some strange behaviour such as when you shutdown linux will halt, but you will actually have to press the power button to remove power from the system as this is normally the job of ACPI.  You may also experience problems suspending etc.

Another option you can try is to add "noapic" instead of "noacpi" it may solve your problem with fewer side-effects, although I doubt it.

Hope this helps

---

