---
title: "duEl-booting prob... (newbie)"
date: 2005-01-17
forum: Installation &amp; Upgrades
---

### Post by aleXL on 2005-01-17
I've installed Ubuntu  around 6 six times over the last two days...

It's wonderful and works great... but... I've been trying to set it up to duEl boot with Win2K but to no avail... I need windoze for clients, at the mo, but perhaps I could convince them to change over...

_My System:_

40Gb HDD Athlon1.7 256Mb RAM (AwardBIOS 2001)

GRUB says it recognises that a Windoze OS exists, and makes allowances for it, but when I select it from teh list, the system just hangs...

I've tried a few methods...

'fDisk /cmbr 1' to wipe the slate clean...

First was to install /boot in hda1 (50Mb), Win2K hda2 (10Gb), / hda3 (10Gb)

Second was to install Win2K hda1 (10Gb), / hda2 (10Gb) + ... with GRUB on mbr

Third was to install Win2K hda1 (10Gb),  /boot hda2 (50Mb), /  hda3 (10Gb)

Fourth was to install / hda1 (10Gb), Win2K hda2 (10Gb) with GRUB on mbr

Fifth was to install Win2K hda1 (10Gb), / hda2 (10Gb) with GRUB on mbr...

Sixth was to install /boot hda1 (50Mb), / hda2 (10Gb), Win2K hda3 (10Gb)


Most of the /  installations were Guided... a few I played with /home and /var... all included a /swap... naturally...

My GRUB format resembled all the ones I've read about in the FAQs and Guides, but doesn't seem to want to play ball... Ubuntu loads okay...

title                 Windows 95/98/NT/2000
root                 (hd0,0)
makeactive
chainloader     +1
savedefault

I did get that Error 17 message once... can't recall which scenario tho'...

I've now gone for a WinXP installation (from where I'm writing this)... installed this evening... ready to install Ubuntu... any advice for me b4 I start?

Have I been really thick somewhere?

---

### Post by hardcandy on 2005-01-17
You do not need a /boot partition on hda1. Make two partiions, the first one NTFS and one free space. Install WinXP on hda. Let it finish. Then install Ubuntu in the free space. Grub will install itself in the Master Boot Record at the beginnig of the disk.

---

### Post by aleXL on 2005-01-18
OK, have done

hda1 WinXP (never used b4 as h8 Win ethics)
hda2 /
10Gb UNpartitioned (to be used as a 'noman's land')
swap

Will update as and when...

---

### Post by aleXL on 2005-01-18
(!!) Install GRUB boot loader to hard disk?

Install Grub Boot to mbr?

The following Operating Systems have been detected on this computer...
WinNT,2K,XP

default YES... to mbr

Shall I?

---

### Post by aleXL on 2005-01-18
Okl...

Couldn't wait... mbr choice made...

So... result...

Ubuntu loads perfectly... want s to update etc... so do...

but... XP... no go... just a skeletal grub menu with cursor prompt flashing around willy nilly....

"Ctrl + Alt + Del...",  "Ubuntu...", "Thank goodness..."

Will send GRUB info at next available mo.... anything else reqd? fstab... how?

---

### Post by aleXL on 2005-01-19
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
## by the debian update-grub script except for the default optons below

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
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by aleXL on 2005-01-19
When I select XP, GRUB is giving me:


Booting command-list


root (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

_ (flashing cursor)


And that's it... just hangs...

---

### Post by aleXL on 2005-01-20
Tad embarassed...

LBA... just found it in the BIOS...

It did seem as if the BIOS had to Auto... but then... I was wrong...

Well, that's that for now...

---

