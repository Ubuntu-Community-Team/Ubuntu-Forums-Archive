---
title: "[SOLVED] &amp;quot;Can not mount the selected partition &amp;quot; please help"
date: 2008-09-25
forum: General Help
---

### Post by amr321123 on 2008-09-25
hi guys , I've ubuntu and windows xp . when I switch on my computer and select ubuntu from boot menu , it says "Can not mount the selected partition "

Please help me

---

### Post by caljohnsmith on 2008-09-25
OK, boot your Ubuntu Live CD, go to Applications > Accessories > Terminal, and type the following:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And also post the output of:
```
sudo blkid
```
Let me know how that goes or if you get any errors.

---

### Post by amr321123 on 2008-09-27
ok 

input :
```
sudo fdisk -lu
```
output:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf45faac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    13864094     6932016    7  HPFS/NTFS
/dev/sda2        13864095   156248189    71192047+   f  W95 Ext'd (LBA)
/dev/sda5        13864158    56837969    21486906    7  HPFS/NTFS
/dev/sda6        56838033    81369224    12265596    7  HPFS/NTFS
/dev/sda7        81369288    91843604     5237158+  83  Linux
/dev/sda8        91843668    93948119     1052226   82  Linux swap / Solaris
/dev/sda9        93948183   121290749    13671283+   7  HPFS/NTFS
/dev/sda10      121290813   156248189    17478688+   7  HPFS/NTFS
```


input:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
output:
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
# kopt=root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,8)
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


input:
```
sudo blkid
```
output:
```
/dev/sda1: UUID="40B0A160B0A15D62" TYPE="ntfs" 
/dev/sda5: UUID="0600BB1E00BB1421" LABEL="MARWA" TYPE="ntfs" 
/dev/sda6: UUID="7608ECC408EC8489" LABEL="AMR" TYPE="ntfs" 
/dev/sda7: UUID="048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7" TYPE="ext3" 
/dev/sda8: UUID="1b0375c7-93d7-453e-9d5c-3b624756576f" TYPE="swap" 
/dev/sda9: UUID="3E8CF70C8CF6BD89" LABEL="GENERAL" TYPE="ntfs" 
/dev/sda10: UUID="A28CB5328CB501B9" LABEL="HALA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
```


please help me

---

### Post by drs305 on 2008-09-27
It looks like the UUID is correct but that grub is pointing to the wrong partition (hd0,8). For both the drives and the partitions, grub starts counting at 0. So for sda7, the seventh partition on the first drive, the designation should be (hd0,6).

Mount the partition (as per the previous instruction):
```

sudo mount /dev/sda7 /mnt
sudo cp /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst.bak
gksu gedit /mnt/boot/grub/menu.lst

```

Change this:
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

```

To this:
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(**hd0,6**)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(**hd0,6**)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=048fb170-9bf4-4ee0-b5ec-3f2a64f8d1e7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(**hd0,6**)
kernel		/boot/memtest86+.bin
quiet


```

Save and reboot.

If this doesn't solve things, it may be because the partition is not marked as bootable. You can change the flags in gparted by selecting the partition and then Partition, Manage Flags.  If you still have problems, report back any errors you get after accomplishing the above.

---

### Post by amr321123 on 2008-09-27
thank you very much drs305 , my problem has been solved .
thank you again .

---

