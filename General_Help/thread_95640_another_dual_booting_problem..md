---
title: "another dual booting problem."
date: 2005-11-27
forum: General Help
---

### Post by detyabozhye on 2005-11-27
Hi, I've tried searching the web and the forum and tried most suggestions on how to get GRUB to load Windows, or whatever it's called (switching jumbers on hard drives gets boring). But no matter what I tried, when I try to boot Windows from the GRUB menu, it will flash a little text at the top (I didn't notice it the first few times, too fast), then the screen will be just black, and nothing works untill I hit the power button (no reset on this box). I have Linux on the master and Windows on the slave (hdb1) (yeah, it's a slave, muahahahaha). Here's my boot list thingie as it looks right now.
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
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by 23meg on 2005-11-27
Did you try removing those map lines on the last entry?

---

### Post by detyabozhye on 2005-11-27
I think I did once, but I'll try again monday, since I'm going to go to sleep now.

---

### Post by Original Brownster on 2005-11-27
Try this, I have 2000 on /dev/hdb :

title           Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader     +1


I have the 'savedefault' and 'makeactive' hashed out.

---

### Post by detyabozhye on 2005-11-28
[QUOTE=23meg]Did you try removing those map lines on the last entry?[/QUOTE]
Here's what I got trying that:
```
Booting 'Microsoft Windows XP Professional'

root (hd1,0)
   Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

For some reason it won't boot normally now, it only boots in verbose mode.

---

### Post by detyabozhye on 2005-11-28
[QUOTE=Original Brownster]Try this, I have 2000 on /dev/hdb :

title           Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader     +1


I have the 'savedefault' and 'makeactive' hashed out.[/QUOTE]
Here's what I got:
```
   Booting 'Microsoft Windows XP Professional'

chainloader +1

Error 13: Invalid or unsupported exacutable format

Press any key to continue...
```

---

### Post by Original Brownster on 2005-11-29
Hi,
You need the 'rootnoverify' instead of 'root'
If you haven't already, try using the same commands  as I have and just change the disk parameters as required.

Regards

---

