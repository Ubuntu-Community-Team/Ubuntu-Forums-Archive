---
title: "Grub, Booting into Windows Extremely Slow"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by cholick on 2005-12-30
First of all, I would like to thank everyone at the board - searching here has solved a great many of my problems.  After a great deal of looking, though, I cannot find a solution to the problem I'm having now.

The issue is this:
When I boot into Windows XP, I stare at a blank screen for about 1min 45seconds before I see windows start to load.  Though I could probably live with it, it is quite annoying.

The steps that have lead up to this (possibly not 100% accurate, some of this was quite a while back).
[LIST]
[*]I had Ubunto co-existing with windows for several months and everything was shiny.
[*]I added a second hard drive.  After going into windows and formatting ntfs, I couldn't boot.  I realized that both drives were on cable select and I'd hooked the newer drive up to the master choice.  I changed bios to boot from hdd-0 to hdd-1 and all was happy again.
[*]I decided to do a clean Ubuntu install (things were a little bit strange after months of messing around).  This all went fine - I didn't change any of the partitions, just formatted and put the new install where the old was.  However, when I rebooted I got grub error 25, disk read error.  This happend when trying to boot into all grub choices.  After a few moments of panic, I decided to switch the cables on the hard drive and change back bios, so that the drive with the os's was hdd-0 again.  To my surprise, this actually worked.
[*]And that brings me to now:  Everything seems just fine.  In Ubuntu, the drives are all readable.  Windows sees everything, and can read all the ntfs partitions.  It says that linux partitions are 'healthy', but can't read them.  However, I have this extreme delay booting into Windows.  This delay did not exist before.
[/LIST]
I'm not sure what to try from here.  I've re-installed grub (grub-install /dev/hda).  I'm a little gun-shy at this point - after the brief panic where I couldn't boot into anything I'm a little more cautious about data loss.  Any advice would be appreciated.  Thanks.

fdisk -l output
**/dev/hda**
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12523   100590966    7  HPFS/NTFS
/dev/hda2           12524       14347    14651280   83  Linux
/dev/hda3           14348       14593     1975995   82  Linux swap / Solaris

**/dev/hdb/**
Disk /dev/hdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      310097   156288856+   7  HPFS/NTFS

**/etc/boot/grub/device.map**
(hd0)   /dev/hda
(hd1)   /dev/hdb

**/etc/boot/grub/menu.lst**
(the 4th from the last line used to read 'root	(hd0,0)', I changed it because of something I read elsewhere but this didn't help)

[HTML]
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
[/HTML]

---

