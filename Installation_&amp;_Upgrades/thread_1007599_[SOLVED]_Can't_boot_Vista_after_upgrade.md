---
title: "[SOLVED] Can't boot Vista after upgrade?"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by xr440dude on 2008-12-10
I've been poking around the forums for a while and haven't seen a fix, so forgive me if I'm in the wrong forum or there's already been a fix posted.

I've been setup with Hardy and Vista dual-booting on my laptop for a few months now.  Everything has been going quite well until a few weeks ago when I noticed Vista wouldn't boot anymore.  When I try from the GRUB menu, it just resets my comp and restarts GRUB again.  Hardy still boots and works well.

The problem seems coincident with an automatic Ubuntu update I got at the end of November, but I can't say for sure. 

I've checked the menu.lst file and it seems correct, but the date of the file is about the time I got the aforementioned update.

Any help?:confused:

---

### Post by caljohnsmith on 2008-12-10
How about first posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there if you want.

---

### Post by xr440dude on 2008-12-10
caljohnsmith, thanks for the reply.  Here's what I have;

FDISK

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e08c48d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    21896594    10948266    7  HPFS/NTFS
/dev/sda2   *    21896595   312576704   145340055    7  HPFS/NTFS
/dev/sda3       312576705   625137344   156280320   83  Linux
```


MENU.LST

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
# kopt=root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f3fb75e2-2dde-433d-bc30-160263030f06 ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by caljohnsmith on 2008-12-11
Are you using that second Vista entry in your Grub menu to boot Vista? Because it looks like that should be the correct one. The first Vista entry looks like your Vista recovery partition. If you want, you could make that clear in your menu.lst by doing:
```
gksudo gedit /boot/grub/menu.lst
```
And then change the "title" line of the first Vista entry to something like:
```
[COLOR="Blue"]title Windows Vista Recovery Partition[/COLOR]
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Anway, it appears you have a Windows problem rather than a Grub problem at this point if you have been using your second Vista entry in the Grub menu to boot Vista (the entry that uses (hd0,1)). Since you have a recovery partition and probably not a Vista Install CD that came with the computer, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would boot that and choose "Vista Repair". After that, try booting Vista from Grub again, and let me know exactly what happens. We can work from there if you want. :)

---

### Post by xr440dude on 2008-12-11
You are correct, Vista was booting from the second entry (0,1).  I have been reticent to change anything since I'm still very new to Linux, but It'll be better if I rename the first entry as you suggested.

I'll give the Vista Repair a try and let you know how it goes.

Thanks for the advice.

---

### Post by xr440dude on 2008-12-11
Well, that did it!  The recovery told me there was something wrong with my boot options, but no details.  I let it fix the problem automatically and now it's happy again.

I sure wish I knew what caused the problem so I could try and avoid it in the future!  I'll keep the recovery disk on hand to help if I need it again.

caljohnsmith - Thanks so much for you help!

---

### Post by caljohnsmith on 2008-12-11
Glad to hear that did the trick; if you have any similar problems in the future with Vista, you might want to browse the Vista partition from Ubuntu and make sure that there aren't any Ubuntu files/directories there, because you did mention that the problem seemed coincident with updates in Ubuntu. I don't think that would be the issue, but it wouldn't hurt to check if you have any more Vista problems. Anyway, cheers and have fun with Vista and Ubuntu. :)

---

