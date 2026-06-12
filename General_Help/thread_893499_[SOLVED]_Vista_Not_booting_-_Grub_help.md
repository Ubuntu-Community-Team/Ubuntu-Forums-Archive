---
title: "[SOLVED] Vista Not booting - Grub help"
date: 2008-08-18
forum: General Help
---

### Post by BCawley on 2008-08-18
I searched a found a similar thread, but i didnt have permission to post, anyway off i go........


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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,3)/boot/grub/splashimages/UbuntuOrangeSplash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=59488bad-24cb-45f6-9c12-6a5200e498d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash vga=795

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title   Vista
root (hd0,1)
savedefault
makeactive
chainloader +1
boot

title   Vista Recovery
root (hd0,0)
savedefault
makeactive
chainloader +1
boot


title		Debian GNU/Linux, kernel 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=59488bad-24cb-45f6-9c12-6a5200e498d0 ro quiet splash vga=normal
initrd		/boot/initrd.img-2.6.24-21-generic
boot

title		Debian GNU/Linux, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=59488bad-24cb-45f6-9c12-6a5200e498d0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST





```

My grub, as im sure your aware. 

my Gparted screenie is attached.

Recently i changed to the .21 kernel, and then shortly afterwords i done some awkward partitioning, adding a few GB's to / and the vista partition.

Help as to why vista isnt booting would be greatly appreciated, its been a bad day for me today 	](*,)

Also on booting ubuntu, there was one [fail] mentioning windows, will post more info if deemed necessary.
Thanks!

---

### Post by BCawley on 2008-08-18
ok then a refined question may help me find my solution. As a rule of thumb, is the first partition (0,0) second (0,1) third (0,2) etc?

Also now, regardless of which vista i boot into
 (0,0)- Recovery or 
(0,1) Vista
It boots to the recovey partition.

Help appreciated :(

---

### Post by BCawley on 2008-08-18
Got it fixed anywho, was moreso a vista problem.
Downloaded and burned a [vista recovery iso]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), popped it in and changed boot order in the bios. It loaded some files and vista went through chkdisk, restarted and all booted well.

Pfft Ubuntu has strong support community? All I needed was google. Close me Please! :tongue:

---

### Post by Test_ on 2009-05-01
Thx man! I was looking for solution of this problem and finally I spotted ur post. I'm downloading Windows Vista Recovery Disc. I hope this will solve my problem. Fingers crossed :)

Edit:
Solved! This disc DID help me. Thanx again.

---

