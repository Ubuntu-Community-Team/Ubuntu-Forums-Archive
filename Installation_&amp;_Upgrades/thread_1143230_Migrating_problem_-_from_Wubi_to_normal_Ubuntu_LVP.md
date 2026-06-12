---
title: "Migrating problem - from Wubi to normal Ubuntu LVPM"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by mke on 2009-04-29
I installed Wubi on my laptop with two physical hard drives. Wubi is on the same partition with Vista. There is no system on the second hard drive. I decided to move Wubi to normal Ubuntu on the second hard drive (using LVPM). I followed instructions  from [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) and started with  Partition Manager tool and created two partitions: primary formated as ext3 and swap formated as a linux swap also primary. I chose "transfer" from LVPM (I picked up newly created sdb2), everything went successful. Afret restarting I noticed additional grub option
```
title Ubuntu-on-/dev/sdb2
root (hd1,1)
configfile /boot/grub/menu.l
```

After picking this option, next layer of GRUB showed up, almost similar to the previous one. I picked up first option trying to start migrated Ubuntu

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
```

and I encountered something like "error 15: file not found"  and nothing happens

below couple additional information

*from wubi:*

a) from /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

b) from /boot/grub/menu.lst

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
timeout 	10

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
# kopt=root=UUID=D8A41313A412F3AA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=D8A41313A412F3AA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=D8A41313A412F3AA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=D8A41313A412F3AA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=D8A41313A412F3AA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot



title Ubuntu-on-/dev/sdb2
root (hd1,1)
configfile /boot/grub/menu.lst
```


and  information from the Ubuntu afrer migration

a) fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sdb2
UUID=ebae06be-914e-4a73-b65c-b26dd02d9154     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=D8A41313A412F3AA       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sdb3
UUID=a76a2645-0ee0-433b-9d42-4cb88f176d12      none            swap        sw          0   0

```
b) /boot/grub/menu.lst
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
timeout 	10

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
# kopt=root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ebae06be-914e-4a73-b65c-b26dd02d9154  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd0,0)
makeactive
chainloader +1
boot


title Windows Vista (loader)
root (hd0,1)
makeactive
chainloader +1
boot
```


device map
/boot/grub/device.map 
```
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

sudo ls -la /media/disk/dev/disk/by-uuid/
```
lrwxrwxrwx 1 root root   10 2009-04-27 22:39 2C88743C8874071C -> ../../sda2
lrwxrwxrwx 1 root root   10 2009-04-27 22:40 a76a2645-0ee0-433b-9d42-4cb88f176d12 -> ../../sdb3
lrwxrwxrwx 1 root root   10 2009-04-27 18:36 BE948A46948A015F -> ../../sdb1
lrwxrwxrwx 1 root root   11 2009-04-27 18:36 d485b443-5823-4479-b29c-1cd0b2726b64 -> ../../loop0
lrwxrwxrwx 1 root root   10 2009-04-27 18:36 D8A41313A412F3AA -> ../../sda1
lrwxrwxrwx 1 root root   10 2009-04-27 22:40 ebae06be-914e-4a73-b65c-b26dd02d9154 -> ../../sdb2
```


sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18369   147548961    7  HPFS/NTFS
/dev/sda2           18370       19457     8739360    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca7fd385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16551   132945876    7  HPFS/NTFS
/dev/sdb2           16890       19457    20627460   83  Linux
/dev/sdb3           16552       16889     2714985   82  Linux swap / Solaris
```


How can I boot up my normal Ubuntu (after migration)

---

