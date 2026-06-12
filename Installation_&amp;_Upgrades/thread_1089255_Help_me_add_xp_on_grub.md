---
title: "Help me add xp on grub"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by elliotn on 2009-03-06
My haddrive are as follows on bios:

PRIMARY MASTER-20GB (THE ONE WITH UBUNTU)

PRIMARY SLAVE-NONE

SECONDARY MASTER-CD/DVD ROM

SECONDARY SLAVE-40GB(THE ONE WITH XP)
 
Please help me add xp on grup, it has been pain since I took examples i saw here and on google

---

### Post by confused57 on 2009-03-07
In Ubuntu, open a terminal & please post the output of:
```
sudo fdisk -l
```
-l is a small "L"

Someone should be able to help you, if you can provide the
output of the above.

---

### Post by elliotn on 2009-03-07
here is what I get

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde1da92c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2342    18812083+  83  Linux
/dev/sda2            2343        2434      738990    5  Extended
/dev/sda5            2343        2434      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbcacbca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4869    39110211    7  HPFS/NTFS

Disk /dev/sdc: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x3f175b97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7648     1957872    b  W95 FAT32
elliotn@elliotn:~$

---

### Post by elliotn on 2009-03-07
and here is my /grub/menu.lst

> [QUOTE]

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
timeout		3

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
# kopt=root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78d4e77b-ae5f-4f16-b92b-f54aeda58e55

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=78d4e77b-ae5f-4f16-b92b-f54aeda58e55 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		78d4e77b-ae5f-4f16-b92b-f54aeda58e55
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/QUOTE]

---

### Post by confused57 on 2009-03-07
Assuming your 20 Gb Ubuntu drive is set as the first hard drive in your bios boot sequence, here's what you can try:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add this entry for XP at the very end of your menu.lst(after the line ###END DEBIAN AUTOMAGIC LISTS:
```
title              Windows XP
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by elliotn on 2009-03-07
Error 11, urecognised string       

that is what i get

---

### Post by confused57 on 2009-03-07
> **elliotn said:**
> Error 11, urecognised string       

that is what i get
Grub error 11 usually means a typo or syntax error...you can try copying & pasting the xp entry into your menu.lst that I gave you previously.

---

