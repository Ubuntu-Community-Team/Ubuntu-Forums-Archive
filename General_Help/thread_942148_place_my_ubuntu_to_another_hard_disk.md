---
title: "place my ubuntu to another hard disk ?"
date: 2008-10-08
forum: General Help
---

### Post by anhvu2875 on 2008-10-08
i installed Ubuntu 8.10 Beta by WUBI in /D/ hard disk driver and now i wanna bring my Ubuntu to /G/ hard disk driver ( new hard disk i have just bought to use for ubuntu only ), how can i do that , or i need to reinstall Ubuntu ? i hope that i wont need to reinstall Ubuntu , it takes me many times ((( .
THANKS !

---

### Post by pytheas22 on 2008-10-08
There are instructions [here]("http://ubuntuforums.org/showthread.php?t=438591") for what you want to do.

---

### Post by ago on 2008-10-09
move the ubuntu folder and edit ubuntu\disks\boot\grub\menu.lst

root=UUID... -> root=/dev/sdXX

Where XX is the disk and partition, e.g. /dev/sda2 for disk1 partition 2

---

### Post by anhvu2875 on 2008-10-10
**ago**
i move ubuntu folder , and i edited UUID -> ok but my root is still on old disk ?? i dont know how to edit for my root being on right place !

my menu.lst

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
# kopt=root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		()/ubuntu/disks
kernel		/boot/last-good-boot/vmlinuz root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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


```

this is 

```
anhvu2875@anhvu2875-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb810b810

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865       19457   117218272+   f  W95 Ext'd (LBA)
/dev/sda5            4865       12159    58597056    7  HPFS/NTFS
/dev/sda6           12160       19457    58621153+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e4057a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       30401   141797722+   7  HPFS/NTFS
anhvu2875@anhvu2875-desktop:~$ 

```

sdb1 is the hard disk i wanna place my ubuntu on !
THANKS !

---

### Post by ago on 2008-10-10
# kopt=root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro

becomes 

# kopt=root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro

and 

kernel		/boot/vmlinuz-2.6.27-6-generic root=UUID=12A05F68A05F50F9 loop=/ubuntu/disks/root.disk ro quiet splash 

becomes

kernel		/boot/vmlinuz-2.6.27-6-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash

---

### Post by anhvu2875 on 2008-10-10
**ago**
i did but i dont understand this , pls look at the pics 
2 folders are free 68.9GB ( boot and host folders ) , the others are free 21.5 GB ???
i still can see ubuntu folder in /host/ ( the folder created by Wubi to use ubuntu on Wins ) -> so my ''root'' now is on which partition , new sdb1 or old sda1 ???

my menu.lst after editting 

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
# kopt=root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-6-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-6-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-6-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-6-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		()/ubuntu/disks
kernel		/boot/last-good-boot/vmlinuz root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash  last-good-boot
initrd		/boot/last-good-boot/initrd.img

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-5-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-5-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-5-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-4-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-4-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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

```

[IMG]http://i208.photobucket.com/albums/bb133/anhvu2875/Ubuntu/boot.png[/IMG][IMG]http://i208.photobucket.com/albums/bb133/anhvu2875/Ubuntu/host.png[/IMG][IMG]http://i208.photobucket.com/albums/bb133/anhvu2875/Ubuntu/ubuntu.png[/IMG][IMG]http://i208.photobucket.com/albums/bb133/anhvu2875/Ubuntu/usr.png[/IMG]

THANKS for all ur help **ago** !

---

