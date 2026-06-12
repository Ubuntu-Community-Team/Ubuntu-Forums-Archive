---
title: "[SOLVED] Add Windows XP to grub"
date: 2008-08-06
forum: General Help
---

### Post by vdfbelial on 2008-08-06
Hello. I have installed (in the following order) Windows XP, Ubuntu and Vista.
All of them have different partitions.
Ubuntu has a ~ 5gb partition
Vista has a ~ 15gb partition
Xp has a ~ 10 gb partition
all that remains is a whole ntfs partition (120gb hdd)

As you can imagine after I installed ubuntu all was ok. I was able to boot XP and ubuntu from the grub menu.

After I installed Vista grub was gone and I could only boot XP and Vista (through Vista's boot manager).

Now I have reinstalled (after trying to fix this issue a couple of times) Ubuntu and grub is back on. However after this I couldn't boot XP, only Vista and ubuntu.

I tried to add Windows XP to grub using this command:
```
gksudo gedit /boot/grub/menu.lst
```

At the end of the file I added what is marked as bold text:
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
# kopt=root=UUID=86324b3f-825b-4c89-b571-c127d9259dc4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=86324b3f-825b-4c89-b571-c127d9259dc4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=86324b3f-825b-4c89-b571-c127d9259dc4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[B]
title  Windows XP Professional
root   (hd0,5)
savedefault
makeactive
chainloader +1[/B]

```

Here is the output of the *sudo fdisk -l* command:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05955931

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1278    10265503+   7  HPFS/NTFS
/dev/sda2            1279       14593   106952737+   5  Extended
/dev/sda5            1279        1889     4907794+  83  Linux
/dev/sda6            1890        2013      995998+  82  Linux swap / Solaris
/dev/sda7            2014        3932    15409152    7  HPFS/NTFS
/dev/sda8            3932       14593    85637120    7  HPFS/NTFS

```

And here is the output of the [I]root (hd0, <tab>[I] command after entering grub in a terminal:
```

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type unknown, partition type 0x7

```

I just want to be able to boot XP, ubuntu and Vista. What am I doing wrong ?

Thanks in advance.

---

### Post by logos34 on 2008-08-06
Vista takes over the boot process, but it locates the files on the prexisiting, 'active' XP partition. You can't directly boot the XP partition--you have to go through vista.

So, tell me, when you boot Vista via grub, the windows boot manager doesn't give you the additional choice of XP? That's how it's supposed to go

edit:

sda1 * is XP partition (where vista boot manager/files are located)
sda7 is Vista (which is a logical partition...yet another reason for the boot files being on sda1--you can't boot windows on a logical partition unless the boot files are located on a primary partition)

---

### Post by vdfbelial on 2008-08-06
You are right. I am able to boot XP after I choose Vista from grub. Windows Boot Manager then shows two options: Vista and "older" os (xp).

Nevertheless all is ok. Thanks for clearing thing out.

---

### Post by logos34 on 2008-08-06
ok, sounds good.

mark thread as 'solved' (>thread tools)

enjoy

---

