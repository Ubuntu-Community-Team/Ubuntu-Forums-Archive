---
title: "Double ubuntu at booting?"
date: 2008-11-14
forum: General Help
---

### Post by lcruz007 on 2008-11-14
I just re installed Ubuntu after a problem I had with it... In the boot screen, Ubuntu is listed twice... Does that mean Ubuntu was somehow installed twice????? Why is that, how can I fix this little problem?


Thank you

---

### Post by zvacet on 2008-11-14
If you reinstalled it on top of  partition where your first install was then you didn´t install it twice.What you see probably are two Ubuntu kernels.But to be sure type in terminal 

```
sudo fdisk -l
```

Post output here.

---

### Post by lcruz007 on 2008-11-14
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1a74a70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12111    97280000    7  HPFS/NTFS
/dev/sda2           12112       12144      265072+   5  Extended
/dev/sda3           12145       14593    19671592+  83  Linux
/dev/sda5           12112       12144      265041   82  Linux swap / Solaris

Disk /dev/mmcblk0: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1204     1920955+   6  FAT16

```

---

### Post by icanfly0307 on 2008-11-14
Hi,
   I think you are confusing "Ubuntu "version"" with "Ubuntu "version" RECOVERY MODE". The first option is to boot normally into your system while the second option is a Recovery Mode. Hope this helps. :)

---

### Post by lcruz007 on 2008-11-14
Well, I have two recovery modes as well. :p

---

### Post by geirha on 2008-11-14
Post the contents of /boot/grub/menu.lst

---

### Post by lcruz007 on 2008-11-14
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
# kopt=root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
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

```

---

### Post by geirha on 2008-11-14
```

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro single
initrd		/boot/initrd.img-2.6.24-21-generic

```

That's the regular and recovery entries for the newest kernel in Hardy. This was likely installed by an update after your system was installed.
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

```

And those are the regular and recovery entries for the initially installed kernel in Ubuntu 8.04.1.

When a new kernel is installed with a higher version number, you'll get two new such entries. This is because a newer version may have a unforseen bug that will affect you, making you unable to boot for instance, so the previous kernels stays behind so you can still boot the old ones.

If you want the older ones gone, open synaptic and search for "linux-image", then remove the older packages. I recommend you always keep two kernels around though.

---

### Post by lcruz007 on 2008-11-14
I see.... interesting, Ok, thank you! :)

---

### Post by icanfly0307 on 2008-11-14
Well, I found your problem! :KS

Take a look at this and carefully observe the kernel versions...

**THIS:**

*title		Ubuntu 8.04.1, **[I]kernel 2.6.24-21-generic***
root		(hd0,2)
kernel		/boot/***vmlinuz-2.6.24-21-generic ***root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/***initrd.img-2.6.24-21-generic***
quiet
[/I]
[B]
AS OPPOSED TO THIS:[/B]

*title		Ubuntu 8.04.1, **[I]kernel 2.6.24-19-generic***
root		(hd0,2)
kernel		/boot/***vmlinuz-2.6.24-19-generic*** root=UUID=11f68b53-4e40-4ef1-a0ff-d42bad4e1e7a ro quiet splash
initrd		/boot/***initrd.img-2.6.24-19-generic***
quiet[/I]

Basically, you have two kernels (**2.6.24-19** and **2.6.24-21**) installed on ONE operating system. If I were you, I would continue using kernel **2.6.24-21** because it's a more recent version with probably more up to date features. :)

PS. It's actually good to have more than one kernel. If one of your kernels gets corrupted, you'll still have another one that's still working... :lolflag:

---

