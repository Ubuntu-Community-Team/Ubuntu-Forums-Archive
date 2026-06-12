---
title: "[SOLVED] Problems booting XP after Intrepid install"
date: 2008-11-02
forum: General Help
---

### Post by CarpKing on 2008-11-02
I have an Ubuntu/Windows XP dual boot, which worked fine until I installed 8.10 (Intrepid).  This was a fresh install.  Now when I try to boot Windows, I get 
```
Error 13: Invalid or unsupported executable format
```

Everything is installed on my 120 GB IDE drive, but I also have a 500 GB SATA drive that wasn't there last time I installed.  I believe this to be the key.  I've read that Windows doesn't like being on secondary drives (which Grub showed the IDE as), so I unplugged the SATA and now I get the following error when I try to boot Windows:
```
Error 21: Selected disk does not exist
```

It seems that perhaps Grub is trying to boot Windows from the wrong place, but I don't know how to correct that.  

Here is my menu.lst:
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
# kopt=root=UUID=5fdaca2a-66bb-4257-90de-2504273f16e0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5fdaca2a-66bb-4257-90de-2504273f16e0

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
uuid		5fdaca2a-66bb-4257-90de-2504273f16e0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5fdaca2a-66bb-4257-90de-2504273f16e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5fdaca2a-66bb-4257-90de-2504273f16e0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5fdaca2a-66bb-4257-90de-2504273f16e0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5fdaca2a-66bb-4257-90de-2504273f16e0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1

title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

```

And the output of sudo fdisk -lu (when the SATA drive is plugged in it is sda and the other partitions are all sdbx)
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77637763

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29302559    14651248+   7  HPFS/NTFS
/dev/sda2        29302560    43825319     7261380   83  Linux
/dev/sda3       231416325   234436544     1510110    5  Extended
/dev/sda4        43825320   231416324    93795502+  83  Linux
/dev/sda5       231416388   234436544     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Any help would be appreciated.

---

### Post by CarpKing on 2008-11-02
Okay, figured it out.  

I just had to change the Windows entry in menu.lst to:
```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1
```

Now it works, even with the SATA drive plugged in (and taking up sda again).  I'm not sure what the "map" lines are about; they were originally uncommented but commenting them didn't fix the issue.  

Hopefully this thread can help someone in a similar situation.

---

