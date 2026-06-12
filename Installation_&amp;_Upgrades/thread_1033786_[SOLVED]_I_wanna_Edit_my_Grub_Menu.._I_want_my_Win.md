---
title: "[SOLVED] I wanna Edit my Grub Menu.. I want my Windows to be the First one in the Lis"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by sendblink23 on 2009-01-07
Here is my: menu.lst


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
# kopt=root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=def0e49e-ae0e-4f02-ac61-2c320f743bc0

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```


Can anyone convert my File ..  making "Windows XP Media Center Edition" to be the first one in the Grub List?

Thanx =)

---

### Post by thomas228 on 2009-01-07
> **sendblink23 said:**
> Here is my: menu.lst


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
color cyan/blue white/blue

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

title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=def0e49e-ae0e-4f02-ac61-2c320f743bc0

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=def0e49e-ae0e-4f02-ac61-2c320f743bc0 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		def0e49e-ae0e-4f02-ac61-2c320f743bc0
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Windows NT/2000/XP
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows XP Media Center Edition
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1


```


Can anyone convert my File ..  making "Windows XP Media Center Edition" to be the first one in the Grub List?

Thanx =)

Good luck

Tom

---

### Post by Elfy on 2009-01-07
Back up the file and then open it for editing

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.0701
gksudo gedit/boot/grub/menu.lst
```

Cut the whole windows media stanza
> title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Then paste it above the ### BEGIN AUTOMAGIC KERNELS LIST line so that it looks like 

> # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by sendblink23 on 2009-01-07
Thank you that worked perfectly! =)



> **forestpixie said:**
> Back up the file and then open it for editing

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.0701
gksudo gedit/boot/grub/menu.lst
```

Cut the whole windows media stanza


Then paste it above the ### BEGIN AUTOMAGIC KERNELS LIST line so that it looks like

---

