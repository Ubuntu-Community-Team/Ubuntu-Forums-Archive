---
title: "Boot from second hard drive!"
date: 2008-07-23
forum: General Help
---

### Post by DJ-Dark on 2008-07-23
I just mounted a new hard drive inside my Dell with Ubuntu and it has Windows XP on it. I am running GRUB as my bootloader and I was wondering if I could boot off of that hard drive without installing anything like VirtualBox because for some reason my Ubuntu is stuck in low-graphics mode.

Thanks,
DJ-Dark

---

### Post by boblemur on 2008-07-23
hey are you able to paste your 
```

cat /boot/grub/menu.lst
```

just the end of it, not the entire thing, from the boot entries down, if you dont know what they are you can paste the whole thing

---

### Post by DJ-Dark on 2008-07-23
Okay, I pasted that code into my terminal and I dont know what to do next. Im not the smartest with that kind of stuff.

---

### Post by cdtech on 2008-07-23
> **DJ-Dark said:**
> for some reason my Ubuntu is stuck in low-graphics mode.
Thanks,
DJ-Dark

For this you would need to select the "System > Administration > Hardware Drivers" and select the proper Proprietary driver for your video card.

> **DJ-Dark said:**
> 
I just mounted a new hard drive inside my Dell with Ubuntu and it has Windows XP on it. I am running GRUB as my bootloader and I was wondering if I could boot off of that hard

Once in Ubuntu (with the Win XP drive installed) just open a terminal and type "sudo update-grub". This will search for all OS's on the computer and create a list within your menu.lst file..

---

### Post by boblemur on 2008-07-23
ok well it should show u the contence of a file...

and that file contains  all of your boot information...

so paste them here they will look like...

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot


but there will be more of them...

paste them all or if your confused paste the whole file...

also:
```

gedit /boot/grub/menu.lst
```

you may find thats easier to read then the terminal output

---

### Post by DJ-Dark on 2008-07-24
Okay, well for some reason my computer isn't recognising the second hard drive and I can't get out of low graphics mode.

---

### Post by cdtech on 2008-07-24
Could you please explain what you have done thus far?

Did you run the command and were you able to view the /boot/grub/menu.lst file?

---

### Post by DJ-Dark on 2008-07-24
Yeah, I was able to view the contents of that file.

---

### Post by cdtech on 2008-07-24
could you copy and paste here so we can see it please?

---

### Post by DJ-Dark on 2008-07-24
This is what I get.


> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=439cb33d-4605-47f1-9363-f4c653aca200 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by cdtech on 2008-07-24
Do you really use all of those Kernel's? If not you can remove them (the ones you don't use) through synaptics.

As far as your Windows drive, we need to see the output of "sudo fdisk -l" from a terminal.

Then we're almost there.........

---

### Post by DJ-Dark on 2008-07-24
This is what I get when I type sudo fdisk -l into terminal.

> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4778    38379253+  83  Linux
/dev/sda2            4779        4863      682762+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa730e7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         775     5858968+   b  W95 FAT32
/dev/sdb2   *         776        5168    33211080    7  HPFS/NTFS


---

