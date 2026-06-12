---
title: "Kernel panic on 9.04"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by Firedrake445 on 2009-09-20
I'm running Ubuntu 9.04 and After a software update I started receiving this message when booting. (Sorry I'm really not very good at all with Linux yet so I have to post everything I saw.)

Boot from chd 0,0 ext3 390f1d61-678e-42a7-9850-2d2643652c20
Starting up...
[0.296631] Acpi: aborted because bad gzip magic numbers.
[4.166244] Kernel panic- not syncing: VFS: unable to mount root fs on unknown-block (0,0)


The only way I can get linux to boot is if i press esc and select the 9.04-14.

Anyway I can fix this or make it so the 9.04-14 the default boot?

---

### Post by stlsaint on 2009-09-20
chd? how many hdd do you have...
well you can set main boot kernel via startupmanager from synap archive.

---

### Post by Firedrake445 on 2009-09-20
I might of writen down the wrong letter or something. Anywho is it possible to fix the kernel panic?

---

### Post by n0dix99 on 2009-09-20
Go to the file:
```
 $ sudo gedit /etc/grub/menu.lst 
```

Then at final of file is the options of boot, post it.

---

### Post by Firedrake445 on 2009-09-21
The File you mentioned was absolutely blank. Nothing in it at all.

---

### Post by stlsaint on 2009-09-21
Wait...your saying that your menu.lst was completely empty...nothing....are you sure you didnt miss type something!!!
if menu.lst was blank thats some pretty crazy stuff happening. tho he gave you the wrong cmd

type this in terminal:

gksudo gedit /boot/grub/menu.lst 

and post whats in there!

---

### Post by Firedrake445 on 2009-09-22
Okay there was something in there. Just pulled it up. Here it is:



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
default		2

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
# kopt=root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=390f1d61-678e-42a7-9850-2d2643652c20

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=390f1d61-678e-42a7-9850-2d2643652c20 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		390f1d61-678e-42a7-9850-2d2643652c20
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by gentilian on 2009-09-22
There seem to be a lot of threads on these kernel panics on boot, possibly after ~.15 kernel update...

My issue was 'solved' by appending the line "acpi=off" to the end of the grub boot commands for the latest kernel. Clearly not a best case scenario on a laptop, but it's got me running again...

---

### Post by suicidalsnowman on 2009-09-23
I had the exact same problem, I followed the advice in this thread [http://ubuntuforums.org/showthread.php?t=984419](http://ubuntuforums.org/showthread.php?t=984419)

Simply boot into a different kernel, or a rescue disk. From the rescue prompt, run this command (as root):

     Code:
     update-initramfs -k all -c -v

---

