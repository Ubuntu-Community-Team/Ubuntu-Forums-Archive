---
title: "Can't boot from this partition (USB Ubuntu)"
date: 2008-08-12
forum: General Help
---

### Post by KnightOnline on 2008-08-12
I've followed the "how-to" on how to install Ubuntu on a usb device, and installed it on a 60GB external hardrive. My laptop supports booting by USB, but when I try to boot to it it grub gives me a messeage saying "cannot boot from this partition"

Any ideas on why?

---

### Post by justleen on 2008-08-12
is the bootable flag set?
is grub installed corectly?
is grub pointing to the right disk/partition?

---

### Post by KnightOnline on 2008-08-12
> **justleen said:**
> is the bootable flag set?
is grub installed corectly?
is grub pointing to the right disk/partition?

How do I check if the bootable flag is set?

When installing ubuntu i pointed grup at the /dev/sdb which was my USB drive

---

### Post by nazish on 2008-08-12
run the command> fdisk -l if an asterix " * " appears then the boot flag is set and you can boot through the partition.
 
also can you just post the contents of your menu.lst file. to do this type this in the terminal
> gedit /boot/grub/menu.lst

---

### Post by KnightOnline on 2008-08-12
fdisk -l doesn't show anything

my menu.lst is as follows:

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
# kopt=root=UUID=cb5a4360-c3be-4dbb-84f8-00f8731bc772 ro

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
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cb5a4360-c3be-4dbb-84f8-00f8731bc772 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cb5a4360-c3be-4dbb-84f8-00f8731bc772 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by KnightOnline on 2008-08-12
I was able to get fdisk to work, here's the result:

> Disk /dev/sda: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d4c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2496    20049088+  83  Linux
/dev/sda2            2497        2610      915705    5  Extended
/dev/sda5            2497        2610      915673+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bc58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7108    57094978+  83  Linux
/dev/sdb2            7109        7296     1510110    5  Extended
/dev/sdb5            7109        7296     1510078+  82  Linux swap / Solaris


/dev/sda is the hard drive of the computer i'm using, and has Ubuntu 8.04 installed, 
/dev/sdb is the external hard drive i'm trying to get Ubuntu to work on

---

### Post by caljohnsmith on 2008-08-12
Just out of curiosity, why don't you have any entries in your menu.lst for your Ubuntu that's on your internal HDD (sda1 or (hd0,0))? I'm wondering because you most likely have two menu.lst files, one in Ubuntu on the internal HDD and one in the Ubuntu on your USB HDD. We need to know which menu.lst is getting loaded on startup to solve your problem.

If you do have another menu.lst in the other Ubuntu, would you please post that? And also make it clear which menu.lst it is--whether it is from sda1 or sdb1.

---

### Post by KnightOnline on 2008-08-12
> **caljohnsmith said:**
> Just out of curiosity, why don't you have any entries in your menu.lst for your Ubuntu that's on your internal HDD (sda1 or (hd0,0))? I'm wondering because you most likely have two menu.lst files, one in Ubuntu on the internal HDD and one in the Ubuntu on your USB HDD. We need to know which menu.lst is getting loaded on startup to solve your problem.

If you do have another menu.lst in the other Ubuntu, would you please post that? And also make it clear which menu.lst it is--whether it is from sda1 or sdb1.

There isn't any entries for the Ubuntu installed on the machine itself because I disconected the hardrive when I did the USB installation to make sure nothing would get stored in the computer and the install would be truly independent.

I know its the USB grub that's getting loaded because I have tested it on a windows machine now and it has the same result:

Error 17: Cannot boot from partition

---

### Post by caljohnsmith on 2008-08-12
Well if the Grub you are loading on startup is from the USB HDD, then I believe all you need to do is change all your Ubuntu menu entries to be (hd0,0) instead of (hd1,0), since you are using the Grub on the same HDD as the Ubuntu you are trying to boot. Give that a try and let me know if it works.

---

