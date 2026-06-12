---
title: "Must have USB stick inserted or get Grub error 21"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by mikemunsil on 2009-09-18
My boss gave me a new Toshiba laptop to use, running Vista Home Premium, and I promptly set it up to dual-boot Ubuntu 9.04. All good so far.

Then I decided to make a Live USB version and used the Ubuntu install disk to do so, on the same computer.

Now, EVERY time I boot that computer, I have to have the USB stick inserted or it won't boot into anything, and gives me varying errors:

Grub error 25
Grub error 21

It doesn't always give me the same error, or both errors.

Any idea of where to start looking to fix this would be vastly appreciated.  The ideal situation would be to end up with the Vista/Ubuntu dual-boot working without having to insert the usb drive.  If necessary, I can live with just Vista on the machine.

Please advise!

Here are the menu.lst files for the hard drive and the usb drive:

[INDENT]```
**Hard Drive**

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
# kopt=root=UUID=843960d3-5400-499b-a649-9c8d6e9819f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=843960d3-5400-499b-a649-9c8d6e9819f6

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		843960d3-5400-499b-a649-9c8d6e9819f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=843960d3-5400-499b-a649-9c8d6e9819f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		843960d3-5400-499b-a649-9c8d6e9819f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=843960d3-5400-499b-a649-9c8d6e9819f6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		843960d3-5400-499b-a649-9c8d6e9819f6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root




# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1
```[/INDENT]

[INDENT]```
**USB Drive**

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
# kopt=root=UUID=fc42630c-3b94-4c33-805a-b0a250b29363 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fc42630c-3b94-4c33-805a-b0a250b29363

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		fc42630c-3b94-4c33-805a-b0a250b29363
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fc42630c-3b94-4c33-805a-b0a250b29363 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fc42630c-3b94-4c33-805a-b0a250b29363
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fc42630c-3b94-4c33-805a-b0a250b29363 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fc42630c-3b94-4c33-805a-b0a250b29363
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=843960d3-5400-499b-a649-9c8d6e9819f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=843960d3-5400-499b-a649-9c8d6e9819f6 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

[/INDENT]

---

### Post by mikemunsil on 2009-09-18
By the way, I just found the following at PenDriveLinux. It appears to apply, but does anyne here have any comments?

> During the Ubuntu USB hard drive installation process, Grub was accidently moved from the internal hard drive to their external hard drive, rendering the original Linux system unbootable without the external drive plugged in. When attempting to boot from the original Debian Linux system, they would encounter the Grub Error 21 shortly after the Grub 1.5 boot process.

The good news is that the fix to repair Grub on the original system was quite simple and is illustrated below:

Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE devices

---

### Post by mikemunsil on 2009-09-18
Log of applying the fix above:

> fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93c5eb0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       31386   250567676    7  HPFS/NTFS
/dev/sda3           37760       38914     9266176   17  Hidden HPFS/NTFS
/dev/sda4           31387       37759    51191122+   5  Extended
/dev/sda5           31387       37493    49054446   83  Linux
/dev/sda6           37494       37759     2136613+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3963 MB, 3963617280 bytes
255 heads, 63 sectors/track, 481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e457d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         453     3638691   83  Linux
/dev/sdb2             454         481      224910    5  Extended
/dev/sdb5             454         481      224878+  82  Linux swap / Solaris


> grub-install /dev/sda

Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda

And it worked!  I had to try two times. The first time, I made the mistake of using the following:

>  grub-install /dev/sda5

instead of:

>  grub-install /dev/sda

Thanks for all the help! :)

Hopefully someone else as confused as I will find this useful.

Mike

---

### Post by Professoryk on 2009-10-10
_I had same problem  and_ i solved my problem with your post and solution method:).

_ __Thank you _[mikemunsil]("http://ubuntuforums.org/member.php?u=132722")

Y.K

---

