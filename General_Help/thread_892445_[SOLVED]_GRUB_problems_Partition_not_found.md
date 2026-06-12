---
title: "[SOLVED] GRUB problems: Partition not found"
date: 2008-08-17
forum: General Help
---

### Post by boombox1387 on 2008-08-17
Right now I'm dual booting WinXP and Ubuntu Hardy.  Just for fun I reinstalled Hardy from a CD on the same partition that it had been on.  Now when I start up the computer, I get an Error (number 22, I believe) telling me that it can't find the partition when I choose Ubuntu.  

When I choose XP it tells me that the disk is not bootable and I should insert the system disk.  I press enter a couple times and it takes me back to a GRUB screen that works flawlessly for both the Ubuntu and Windows XP options.

Anyone know what happened or how I can fix it?

---

### Post by caljohnsmith on 2008-08-17
Your situation sounds a bit strange, but how about booting your Ubuntu Live CD, open a terminal, and do the following:
```
sudo fdisk -l
```
That will show your partitions, look for the one that says "linux" under "system", and that should be your Hardy partition in the form /dev/sdaX. Use that to do:```

sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the output of all the commands above.

---

### Post by boombox1387 on 2008-08-17
Thanks for the help.  Here's what happened in Terminal, although I must admit it doesn't mean a whole lot to me.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4f7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10160    81610168+   7  HPFS/NTFS
/dev/sdb2           10161       19073    71593672+  83  Linux
/dev/sdb3           19074       19457     3084480   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=83b09cce-3108-42d2-b1e6-d9437a5e5efd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83b09cce-3108-42d2-b1e6-d9437a5e5efd ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83b09cce-3108-42d2-b1e6-d9437a5e5efd ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by caljohnsmith on 2008-08-18
I think the solution to your problem will be as simple as fixing your Windows entry in menu.lst. Please follow these steps:

boot up a Live CD, open a terminal, and do:
```
sudo mount /dev/sdb2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst &

```
Now change your Windows entry (at the bottom of that file) to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
In other words, your Windows partition is on the same HDD as your Ubuntu, so it should use (hd0,0) instead of (hd1,0), and it also doesn't need remapping then. Anyway, save your menu.lst, reboot, and I think you should be good to go.

---

### Post by boombox1387 on 2008-08-19
Thanks a bunch.  I changed (hd1,0) to (hd0,0) and then Windows worked but Ubuntu still didn't, so I changed all of the Ubuntu options from (hd1,1) to (hd0,1) and now everything works beautifully.  Thanks again.

---

