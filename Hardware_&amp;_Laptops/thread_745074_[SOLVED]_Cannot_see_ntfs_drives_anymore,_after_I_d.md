---
title: "[SOLVED] Cannot see ntfs drives anymore, after I did tweaks..."
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by juky on 2008-04-04
.....found on this page:

[http://www.salatti.net/tweak-ubuntu-for-speed/](http://www.salatti.net/tweak-ubuntu-for-speed/)

 I cannot access my ntfs drives, although I can see them both in nautilus and terminal.

So, in Nautilus I got this error:
> "Nautilus cannot display "/media/sdb5"."

And in terminal I get:
> " Transport endpoint is not connected"

Probably something is wrong in either my "menu.lst" or in "fstab" file, which I modified according to the guide from webpage above.

My grub menu (/boot/grub/menu.lst):

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
# kopt=root=UUID=04b5b7d5-6c85-4fd7-91d9-ceb5b4e33a1d ro

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
# defoptions=quiet splash rootflags=data=writeback

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=04b5b7d5-6c85-4fd7-91d9-ceb5b4e33a1d ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=04b5b7d5-6c85-4fd7-91d9-ceb5b4e33a1d ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

And this is mine fstab file (/etc/fstab):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=04b5b7d5-6c85-4fd7-91d9-ceb5b4e33a1d /               ext3    defaults,errors=remount-ro,data=writeback,noatime 0 0       1
# /dev/sda1
UUID=C8B0255FB02554EA /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=14BC872BBC870708 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=AE5835E45835AC49 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=e00f0852-5aea-4ce4-a533-6c8c3b4590ed none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

And fdisk -l:

```

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe849e849

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080        4203      996030   82  Linux swap / Solaris
/dev/sda3            4204        9964    46275232+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x20f920f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      101618    51215188+   7  HPFS/NTFS
/dev/sdb2          101618      620176   261353452+   f  W95 Ext'd (LBA)
/dev/sdb5          101618      620176   261353421    7  HPFS/NTFS

```

Can someone pls. check it and help?

Thanks in advance,
juky

---

### Post by BadPenguin86 on 2008-04-04
To restore your menu.lst, Run this command. ```
sudo update-grub
```
This will let grub update the list. I am not sure that this is the root of your problem, but besides graphical changes, it is probably best to not mess with that list. Run that command and see if that fixes your problem.

---

### Post by juky on 2008-04-04
Although , as described in guide, after modification of menu.lst, I did the command you suggested, I couldn't see ntfs drives. But after I did it for the second time, and did the PC restart, It is possible for me to se NTFS drives.

Thanks for the hint.

---

