---
title: "Ughh..."
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Faraday's Cage on 2007-12-31
Ok, I am not a "complete n00b" but I am stumped. See, I orded Ubuntu, thinking "wouldn't it be nice to dual boot on my laptop (Inspiron 4150)." So I installed it, being careful NOT to erase my MSXP partition and it worked. But now, I can't get into Windows, and all my important stuff is in there. When I boot up, it gives me  ~10 seconds to go into a GRUB menu, or to boot up ubuntu. If I go into the GRUB menu, it gives me the options of ubuntu, ubuntu safe mode, and some weird root-test thingy. Ughh...:confused::(

PS: I'm using Gutsy Gibbon

---

### Post by mmb1 on 2007-12-31
You may very well have deleted your windows partition, but you can check for it by downloading gparted through synaptic.

---

### Post by taurus on 2007-12-31
> **mmb1 said:**
> You may very well have deleted your windows partition, but you can check for it by downloading gparted through synaptic.

Why download gparted when you can use a terminal to look at your partition table.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mmb1 on 2007-12-31
You're right, I'm just not very handy with the command line:)

---

### Post by Faraday's Cage on 2007-12-31
remy@Remylap:~$ sudo fdisk -l
[sudo] password for remy:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1785    14337981   83  Linux
/dev/sda2            1786        3648    14964547+   f  W95 Ext'd (LBA)
/dev/sda5            1786        3506    13823901    7  HPFS/NTFS
/dev/sda6            3507        3648     1140583+  82  Linux swap / Solaris
remy@Remylap:~$ 

So I **didn't** delete my windows partition!

---

### Post by mmb1 on 2007-12-31
So the partition is there, but GRUB doesn't detect it?  I'm not a booting expert, but I'm sure one of the other forum members will be able to guide you through configuring GRUB.

---

### Post by taurus on 2007-12-31
Can you post the outputs of these two commands from a terminal?

```
cat /etc/fstab
sudo cat /boot/grub/menu.lst
```
Perhaps you just need to add an entry for your XP besides those three entries already there:  Ubuntu, recovery mode, & memtest.

---

### Post by Faraday's Cage on 2007-12-31
First command:
```

remy@Remylap:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=40e9c78c-3f28-4937-908d-f857f237cc39 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2630CCEA30CCC253 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=3d261cf1-80b9-41d1-9bfd-af3025d839a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Second command:
```

remy@Remylap:~$ sudo cat /boot/grub/menu.lst
sudo password for remy:
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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=40e9c78c-3f28-4937-908d-f857f237cc39 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=40e9c78c-3f28-4937-908d-f857f237cc39 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=40e9c78c-3f28-4937-908d-f857f237cc39 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by taurus on 2007-12-31
Make a backup copy of your /boot/grub/menu.lst first.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
```
Then, edit it with

```
gksudo gedit /boot/grub/menu.lst
```
and add these lines to the end of it.

```

title  Microsoft Windows XP 
root  (hd0,4)
makeactive
chainloader +1

```
Save it and reboot.  You should now see an option to boot your XP at the bottom of GRUB menu so use the down arrow key to highlight it.

---

### Post by Faraday's Cage on 2007-12-31
I did all of that and I saw the entry in the GRUB menu, but it gave me an error, something like "[dunno] not found."

---

### Post by scxtt on 2007-12-31
you most likely just need to mess around w/ the **root  (hd0,4)** line ... if it's just *usable* partitions, **root  (hd0,2)** might work ... you can edit the grub entries and just keep trying when you box boots w/o having to edit menu.lst each time ...

it also looks like the windows partition, sda5, isn't bootable - i.e. no * in your fdisk -l output ...

---

### Post by ugm6hr on 2007-12-31
> **Faraday's Cage said:**
> 
/dev/sda5            1786        3506    13823901    7  HPFS/NTFS


I thought XP had to be a primary (i.e. not extended) partition in order to boot.  Have you changed the order?

---

