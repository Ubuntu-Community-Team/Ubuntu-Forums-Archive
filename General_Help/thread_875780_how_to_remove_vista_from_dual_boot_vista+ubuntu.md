---
title: "how to remove vista from dual boot vista+ubuntu"
date: 2008-07-31
forum: General Help
---

### Post by JaredLeto on 2008-07-31
I havce decided to move from my dual boot (VISTA + UBUNTU) to ubuntu. (I want UBUNTU to take control of whole harddrive.)
I`ve done some searching, but i could`t find anything that would solve my problem.   

My hard drive is partitioned like this:

```

/dev/sda1 (nfts, formerly Win, now used for data-storing)
/dev/sda3 (ext3, main linux partition
/dev sda4 (linux swap)
/dev/sda2 (ext3, this partiton has BOOT attribute...It used to be nfts,
                 but i formated it to ext3)

```

I would really love to get rid of vista, so please help....thanks in advance

---

### Post by iaculallad on 2008-07-31
Could you post whatever displays when you issue the command below on your terminal:
```

sudo fdisk -l
sudo blkid
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by JaredLeto on 2008-07-31
yea of course. Here`s output 

fdisk -l:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98049804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102400000    7  HPFS/NTFS
/dev/sda2   *       15949       19458    28186624   83  Linux
/dev/sda3           12750       15788    24410767+  83  Linux
/dev/sda4           15789       15948     1285200   82  Linux swap / Solaris

```


sudo blkid:

```
/dev/sda1: UUID="3E487E8B487E4227" TYPE="ntfs" 
/dev/sda2: UUID="fb81dc3a-4dcb-45d5-9563-5a21d774fc7f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="3737e1fe-6359-44a2-ac88-19e8f3b0b776" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="310bfb95-fdd1-46e1-84bc-120ed5d7f892" 

```

cat /boot/grub/menu.lst:


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
timeout         10

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
# kopt=root=UUID=3737e1fe-6359-44a2-ac88-19e8f3b0b776 ro

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
# defoptions=quiet splash noapic

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3737e1fe-6359-44a2-ac88-19e8f3b0b776 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3737e1fe-6359-44a2-ac88-19e8f3b0b776 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3737e1fe-6359-44a2-ac88-19e8f3b0b776 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3737e1fe-6359-44a2-ac88-19e8f3b0b776 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by iaculallad on 2008-07-31
The only way to solve your problem is to edit your menu.lst file and remove the entries pointing to vista as one of your boot options.

```
gksudo gedit /boot/grub/menu.lst
```

You /dev/sda2 is actually formatted as Ext3 as shown by blkid w/c was previously used by your vista partition.

---

### Post by JaredLeto on 2008-07-31
could you tell me what parts should i edit/remove?

---

