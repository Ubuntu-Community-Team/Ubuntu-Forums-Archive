---
title: "Grub dual boot, Error 12: Invalid device requested"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Mcgeesteh on 2009-06-27
Hey,

I just installed an ubuntu/vista dual boot, which was working fine until I expanded my /home (seperate LVM logical volume) with a couple of new disks. Now vista fails to boot with Error 12: Invalid device requested. Output of fdisk and menu.lst below
sde is where Vista resides.

Thanks for any help,
Michael

```
$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=c339d66c-8bc8-42ad-9fd4-ae6467e9736a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5e972ca7-87ef-4101-bf3c-119ebcaf0a8d

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

title		Ubuntu 9.04, kernel 2.6.28-11-server
uuid		5e972ca7-87ef-4101-bf3c-119ebcaf0a8d
kernel		/vmlinuz-2.6.28-11-server root=UUID=c339d66c-8bc8-42ad-9fd4-ae6467e9736a ro quiet splash 
initrd		/initrd.img-2.6.28-11-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid		5e972ca7-87ef-4101-bf3c-119ebcaf0a8d
kernel		/vmlinuz-2.6.28-11-server root=UUID=c339d66c-8bc8-42ad-9fd4-ae6467e9736a ro  single
initrd		/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, memtest86+
uuid		5e972ca7-87ef-4101-bf3c-119ebcaf0a8d
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows Vista (loader)
rootnoverify	(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1
```


```
$ fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96e596e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   83  Linux
/dev/sda2             244       30401   242244135    5  Extended
/dev/sda5             244        1459     9767488+  82  Linux swap / Solaris
/dev/sda6            1460       16048   117186111   83  Linux
/dev/sda7           16049       30401   115290441   8e  Linux LVM

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0b1ebb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       14594   117218304    7  HPFS/NTFS

```

---

### Post by merlinus on 2009-06-27
Have a look in /boot/grub/device.map to make sure all your hdds are listed.

---

### Post by Mcgeesteh on 2009-06-27
They all appear to be there.

```
$ cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
```

---

### Post by merlinus on 2009-06-27
OK.  From what I can see, the vista entry in /boot/grub/menu.lst is correct.

You might try supergrub to boot vista and perhaps permanently fix the problem.  Info here:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

---

### Post by presence1960 on 2009-06-27
you added a couple disks? check your hard disk boot order in BIOS and make sure your disk with Vista corresponds to the menu.lst entry for Vista which is 5th disk. If your vista disk is in another position in boot order try adjusting it's entry in menu.lst to match what position it is in the boot order in BIOS or simply move the Vista disk to 5th in the BIOS boot order.

---

