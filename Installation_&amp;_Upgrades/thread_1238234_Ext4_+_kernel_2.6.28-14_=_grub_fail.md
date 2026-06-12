---
title: "Ext4 + kernel 2.6.28-14 = grub fail"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by andreselsuave on 2009-08-12
Hi there!

That's the thing:

Imade a clean install of ubuntu 9.04 and chose to use ext4. Now I get a message when I try to boot the 2.6.28-14 kernel. 2.6.28-11 works fine. Tried to reinstall grub from a live cd but doesn't work either. Anyone knows how to fix this or alternatively skip this kernel update ?

thanks a lot

---

### Post by Aubergines on 2009-08-12
The exact error message would be handy :D

---

### Post by andreselsuave on 2009-08-12
The exact error reads:

```
[2.068294] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

---

### Post by regala on 2009-08-12
> **andreselsuave said:**
> The exact error reads:

```
[2.068294] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Hum, the associated initramfs seems screwed: no modules for your disk controler has been insmoded (whether filesystems modules are present in the initramfs, remains another question :-) )
Can you post here the content of your /boot/grub/menu.lst ?

br, mathieu

---

### Post by andreselsuave on 2009-08-12
Edited: By the way, the kernel 2.6.28-11 boots with no problems....

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
# kopt=root=UUID=91d6b191-2cc9-4b6a-a1df-6323db1a4ede ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=91d6b191-2cc9-4b6a-a1df-6323db1a4ede

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		91d6b191-2cc9-4b6a-a1df-6323db1a4ede
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=91d6b191-2cc9-4b6a-a1df-6323db1a4ede ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		91d6b191-2cc9-4b6a-a1df-6323db1a4ede
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=91d6b191-2cc9-4b6a-a1df-6323db1a4ede ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		91d6b191-2cc9-4b6a-a1df-6323db1a4ede
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=91d6b191-2cc9-4b6a-a1df-6323db1a4ede ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		91d6b191-2cc9-4b6a-a1df-6323db1a4ede
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=91d6b191-2cc9-4b6a-a1df-6323db1a4ede ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		91d6b191-2cc9-4b6a-a1df-6323db1a4ede
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1

```

---

### Post by regala on 2009-08-13
> **andreselsuave said:**
> Edited: By the way, the kernel 2.6.28-11 boots with no problems....

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

...

```

ok, grub seems to be correctly configured. Might be a problem with initramfs utils that are bugged or poorly configured, since last upgrade. can you post the content of /etc/initramfs-tools/initramfs.conf please ?

br, mathieu

---

### Post by andreselsuave on 2009-08-13
There it is. Thanks for your time! :)
```
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

```

---

### Post by regala on 2009-08-13
> **andreselsuave said:**
> There it is. Thanks for your time! :)


hum, I can't see anything bad. Is there a chance you can put the initrd associated file somewhere one can access it from the internet ?
The content may be rubbish, in case something bad happened when it was generated in the installation procedure of linux-image-whatever-14, OR once more the kernel image + modules deb package uploaded to the repository is screwed and no one checked it (it would not be the first time, and likely the last either)

---

### Post by andreselsuave on 2009-08-13
Bah, It doesnt matter. I don't want to waste our time more with this, I'm in no need to use the 2.6.28-14 kernel. I will stick to the 2.6.28-11 for the moment. Just removing the first two lines from /boot/grub/menu.lst will do, right?

Thanks a lot

---

### Post by johnschong on 2009-08-13
If I use ext4 for the ubuntu, I will part 200mb ext3 for /boot, and the other for ext4

---

### Post by andreselsuave on 2009-08-13
why is that? does ext4 fail for /boot partition?

---

### Post by regala on 2009-08-13
> **andreselsuave said:**
> why is that? does ext4 fail for /boot partition?

no because it wouldn't be able to even read the menu.lst or the stageX files necessary to **start** grub.
the error message is clear about something: it does not recognize any hard drive.

br, mathieu

---

