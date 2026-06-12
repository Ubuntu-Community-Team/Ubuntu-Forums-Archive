---
title: "GRUB still loading 8.04 after upgrade"
date: 2008-11-01
forum: General Help
---

### Post by Kaseas on 2008-11-01
I have my system set up as a dual-boot so that when I boot up, I first select GRUB in the windows vista loader, then select my Ubuntu install in GRUB. After upgrading, I can still only select my 8.04 install, with the old kernel version too. Any ideas as to how I might update this?

---

### Post by caljohnsmith on 2008-11-02
Did you install Ubuntu inside Windows with Wubi or do you have Ubuntu on a separate partition? If you can boot your Live CD, how about opening a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

---

### Post by Kaseas on 2008-11-02
I shrunk my windows partition and installed to a fresh one. The output of ```
 sudo fdisk -lu
``` is ```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24d524d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   211545830   105772884    7  HPFS/NTFS
/dev/sda2       292720365   312576704     9928170    7  HPFS/NTFS
/dev/sda3       211559985   292720364    40580190    5  Extended
/dev/sda5       211560048   289298519    38869236   83  Linux
/dev/sda6       289298583   292720364     1710891   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by caljohnsmith on 2008-11-02
OK, after you've booted into your Ubuntu on your HDD, please post:
```
cat /boot/grub/menu.lst
ls -l /boot
```
Note "-l" is a lowercase L, not a one.

---

### Post by Kaseas on 2008-11-02
cat /boot/grub/menu.lst output:

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
# kopt=root=UUID=066e7365-0311-404b-a7c0-72016b83121b ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=066e7365-0311-404b-a7c0-72016b83121b ro quiet splash init=/sbin/bootchartd
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=066e7365-0311-404b-a7c0-72016b83121b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=066e7365-0311-404b-a7c0-72016b83121b ro quiet splash init=/sbin/bootchartd
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=066e7365-0311-404b-a7c0-72016b83121b ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

ls -l /boot output:
```

total 33048
-rw-r--r-- 1 root root   422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   507665 2008-10-30 01:46 abi-2.6.27-7-generic
-rw-r--r-- 1 root root    80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root    91364 2008-10-30 01:46 config-2.6.27-7-generic
drwxr-xr-x 2 root root     4096 2008-11-01 17:20 grub
-rw-r--r-- 1 root root  7496537 2008-09-26 22:56 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root  7496473 2008-09-24 17:08 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 11408103 2008-11-01 17:17 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root   124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r-- 1 root root   905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  1029585 2008-10-30 01:46 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root     1073 2008-10-30 01:47 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root  1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root  2244464 2008-10-30 01:46 vmlinuz-2.6.27-7-generic

```

---

### Post by caljohnsmith on 2008-11-02
You have the new 2.6.27-7-generic kernel in your /boot folder, so it looks like your menu.lst wasn't updated; when you did the upgrade, and when it asked if it could update your menu.lst, did you decline? That's my guess of why your menu.lst does not have the new kernel. How about doing:
```
sudo update-grub
```
And then look at your menu.lst again, and you should see an entry for the new 2.6.27-7-generic kernel. If that doesn't work, first post the output of the update-grub command above and we can go from there. Otherwise let me know how it goes.

---

