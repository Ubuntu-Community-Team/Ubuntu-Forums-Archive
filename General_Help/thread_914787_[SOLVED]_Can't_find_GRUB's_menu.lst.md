---
title: "[SOLVED] Can't find GRUB's menu.lst"
date: 2008-09-09
forum: General Help
---

### Post by qvyang on 2008-09-09
i have a vista ubuntu dual boot installed in my laptop. 
After i partitioned my vista using a software i got
Grub Loading Please Wait Error 17.

then i looked up a few posts, booted from the LiveCD and did this:

sudo grub
grub
find /boot/grub/stage1
grub> root (hd0,6)
grub> setup (hd0)
grub> quit

after that my boot menu returned, i can boot my vista, but when i choose ubuntu, i got another error:
Grub Error 17: Cannot mount selected partition

so i tried to find my Grub's menu.lst, but i can't find it!

here's the output for following commands:

sudo fdisk -l

Disk /dev/sda: 160.0 GB ...
...
...

Device     Boot   Start    End     Blocks      Id    System
/dev/sda1            1       9      72261      de    Dell Utility
/dev/sda2           10    1315   10485760       7    HPFS/NTFS
/dev/sda3    *    1315    9254   63774267       7    HPFS/NTFS
/dev/sda4         9255   19458   81956269       5    Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5         9255   15296   48532333+      7    HPFS/NTFS
/dev/sda6        19131   19458    2620416      dd    Unkonwn
/dev/sda7        15297   19130   30796573+     83    Linux

Partition table entries are not in disk order


ls -la /boot/grub/menu.lst
ls: cannot access /boot/grub/menu.lst: No such file or directory

Please help!

---

### Post by drs305 on 2008-09-09
From the livecd, to get to your normal menu.lst you must first mount the partition it is on. Open a terminal and then mount your root partition. At that point you will be able to open and edit the grub menu. 

First a note about your partitions. Your fdisk command does not show a swap partition and the only partition which could contain your linux install is sda7. If it is not located on sda7 you will need to change the following entries accordingly.

From the livecd desktop open a terminal (Applications, Accessories, Terminal) and:
```

sudo mount /dev/sda7 /mnt
sudo cp /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst.backup
gksu gedit /mnt/boot/grub/menu.lst

```

---

### Post by qvyang on 2008-09-09
Cool~ i can find my menu.lst now, thanks for that!
now i still can't boot my ubuntu, i still got the error message:
error 17: cannot mount selected partition
here's my menu.lst:

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
# kopt=root=UUID=046d24f9-282f-461b-9790-81a6988f94c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=quiet splash locale=zh_CN

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=046d24f9-282f-461b-9790-81a6988f94c0 ro quiet splash locale=zh_CN
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=046d24f9-282f-461b-9790-81a6988f94c0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1


are there anything wrong?

---

### Post by qvyang on 2008-09-09
i just read the post in 
[http://ubuntuforums.org/showthread.php?t=244788](http://ubuntuforums.org/showthread.php?t=244788)

i got it now! everything back to normal! :D

Thanks!

---

