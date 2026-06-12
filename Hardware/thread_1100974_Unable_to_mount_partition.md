---
title: "Unable to mount partition"
date: 2009-03-19
forum: Hardware
---

### Post by golfer32 on 2009-03-19
I recently installed Ubuntu 8.10 onto my laptop so that I would have dual boot (Windows XP & Ubuntu 8.10).  When I reboot I am unable to boot XP even though it is listed.  I tried to access my files on the XP partition by mounting it inside Ubuntu, but it is unable to mount and I get this warning from GParted:

Failed to startup volume:Invalid argument.
Failed to mount'/dev/sda1':Invalid argument.
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole
disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the orther
way around?

ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sda1' as NTFS failed: invalid
argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a 
partition (e.g. /dev/hda, not /dev/hda1)? This error might
also occur
if the disk was incorrectly repartitioned (see the ntfsresize
FAQ).

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.


Any help would be greatly appreciated.

---

### Post by golfer32 on 2009-03-19
bump

---

### Post by golfer32 on 2009-03-19
bump

---

### Post by Ben_neB on 2009-03-19
Well, I'm pretty new to Linux, but did you defrag your your HDD and check it for errors before you installed Ubuntu? 

If not, I would imagine that there is a possibility that installing Ubuntu may have messed up your XP install. 

If you've got an XP disc, you could try repairing your install, I would think.

---

### Post by golfer32 on 2009-03-19
bump

---

### Post by schmoo2x on 2009-03-20
You're booting with GRUB, right? is GRUB pointing to that same partition that's failing on a mount?

What specific errors are you getting when you try to boot from the XP partition?

---

### Post by golfer32 on 2009-03-20
> **schmoo2x said:**
> You're booting with GRUB, right? is GRUB pointing to that same partition that's failing on a mount?

What specific errors are you getting when you try to boot from the XP partition?

Yes I am booting with grub when I try to boot windows it says that it is not bootable. I used the windows recovery console and windows could not recognize that there was a system on the partition.

---

### Post by schmoo2x on 2009-03-20
My instinct says that your partition table is broken for the NTFS volume... sadly, the only solution that I know of for that is to re-format the partition. I imagine this is an unacceptable solution for you.

However, in the event that there's just some kind of mis-configuration, what's your /boot/grub/menu.lst ? also, what do you get when you run "sudo fdisk -l"?

---

### Post by golfer32 on 2009-03-20
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
timeout		10

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
# kopt=root=UUID=73542ae9-b0df-48bd-a9b7-cc1a4638f897 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73542ae9-b0df-48bd-a9b7-cc1a4638f897

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

title		Ubuntu 8.10 Ultimate 2.1
uuid		73542ae9-b0df-48bd-a9b7-cc1a4638f897
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=73542ae9-b0df-48bd-a9b7-cc1a4638f897 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-12-generic
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4865    39078081    7  HPFS/NTFS
/dev/sda2            4866        9729    39070080   83  Linux

---

### Post by schmoo2x on 2009-03-20
I'm sorry, friend - I think you've got a broken partition. I'm no expert on repairing NTFS partitions, but I think something like Partition Magic may be your only hope.

Someone please correct me if I'm wrong!

---

### Post by golfer32 on 2009-03-20
K thanks I had the feeling it was broken.

---

### Post by schmoo2x on 2009-03-20
no prob - sorry I don't have any better news.

Let me know if you find something that will pull the data off of the broken partition, I'd be interested in keeping it around for a rainy day.

---

