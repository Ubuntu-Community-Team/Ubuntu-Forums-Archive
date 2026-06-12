---
title: "[SOLVED] Another GRUB error 17 thread :'("
date: 2008-09-15
forum: General Help
---

### Post by dtd2932 on 2008-09-15
Hey. I've read like 20 different threads on people with this problem, but none of their solutions worked for me so I had to be that guy and create another one...

I'm running Vista on a 150gb raptor hd, then have a 500gb data hard drive, and just installed ubuntu 8.04 on a 320gb hd. I've tried reinstalling numerous times using different locations for the boot loader, but to no avail. I have also tried reinstalling grub from the livecd, which also didn't change anything. And in the boot menu, the line of code is pointing to the correct device hd(2,0).

From what I've seen in the other threads, I'll just go ahead and save time and post my menu.lst and fdisk -l

```

MENU.LST:

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
# kopt=root=UUID=dcbb73c1-fc9d-4264-9e0f-7b140fe5b56d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash xforcevesa

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dcbb73c1-fc9d-4264-9e0f-7b140fe5b56d ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dcbb73c1-fc9d-4264-9e0f-7b140fe5b56d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

FDISK -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd2c26d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       58889   473024512    7  HPFS/NTFS
/dev/sda2   *       58889       60802    15360000   af  Unknown

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8a33ad4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18242   146521088    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41024101

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       37438   300720703+  83  Linux
/dev/sdc2           37439       38913    11847937+   5  Extended
/dev/sdc5           37439       38913    11847906   82  Linux swap / Solaris

```

It looks like grub is set to the correct hd... 2,0 being /dev/sdc1 (I think...?), and that's where grub was set to install. Anyways, any help is much appreciated... I'll be here for the next hour, but then gotta go to class and will be back again at 8:30 if you need more info from me.

Thanks

---

### Post by caljohnsmith on 2008-09-15
So on start up do you get the Grub menu, choose Ubuntu, and then get error 17? Or do you get error 17 even before you get a Grub menu? If it is the former, next time on start up select the Ubuntu entry, press "e" to edit it, select the line that says "root (hd2,0)", change it to "root (hd1,0)", return to save the change, then press "b" to boot. If that doesn't work, use (hd0,0) instead. 

Although the above advice may seem crazy, Grub on start up sees the order of HDDs the same as the BIOS boot order, and that is not necessarily the same as the device order in Ubuntu's /dev directory. Thus your sdc drive may not be (hd2) in Grub's Convoluted World; it could be (hd1) or even (hd0) depending which HDD you are booting from. 

Let me know how it goes, or if you run into additional problems.

---

### Post by dtd2932 on 2008-09-15
Haha I can't believe it was that retarded simple. I was messing with it for like 4 hours last night using stuff that worked for other people... The hard drive is the 1st boot device in my BIOS, so it had to be changed to hd(0,0).

Thanks so much.

---

