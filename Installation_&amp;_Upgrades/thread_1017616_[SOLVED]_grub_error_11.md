---
title: "[SOLVED] grub error 11 ?"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by mano cazalet on 2008-12-21
hello all,

after last kernel update I run into a grub error:

error 11
unrecognised device string

which sounds weird because I haven't messed with partitions at all before this

I`ve already tried to reinstall grub from live cd
```
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
``` 

without succes.

I`d like to ask you to help me finding out what went wrong and how can I recover my ubuntu install.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bdf7c14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326    6  FAT16
/dev/sda2   *          12        8196    65746012+   7  HPFS/NTFS
/dev/sda3            8197       12161    31848862+   5  Extended
/dev/sda5            8197       11992    30491338+  83  Linux
/dev/sda6           11993       12161     1357461   82  Linux swap / Solaris

```

menu.lst:

```
gfxmenu /boot/grub/message.suse
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
# kopt=root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ac46354f-2da9-4f31-9358-3b15b46d8175

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
##      altoptions=(single-user) single
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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-10-generic
root		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro quiet splash
initrd		/boot/initrd.img-2.6.27-10-generic

title		Debian GNU/Linux, kernel 2.6.27-10-generic (recovery mode)
root		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro single
initrd		/boot/initrd.img-2.6.27-10-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1
```

---

### Post by unutbu on 2008-12-21
Boot from the LiveCD, open a terminal and try this:
```
sudo grub
root (hd0,4)
setup (hd0)
```

Note "root (hd0,4)" rather than "root (hd0,1)".

(hd0,4) is /dev/sda5, which is where fdisk says your Linux partition resides.

---

### Post by Elfy on 2008-12-21
Edit the file so that root is replaced with uuid

> uuid		ac46354f-2da9-4f31-9358-3b15b46d8175

You can try from grub - e will allow you to edit the line or alternatively boot a livecd and do so from there.

Link to temporary editing of grub file - 
[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu)
Once you've got into the system edit the rmainder of the lines to read uuid

---

### Post by mano cazalet on 2008-12-21
thx for your replies

> **unutbu said:**
> Boot from the LiveCD, open a terminal and try this:
```
sudo grub
root (hd0,4)
setup (hd0)
```

Note "root (hd0,4)" rather than "root (hd0,1)".

(hd0,4) is /dev/sda5, which is where fdisk says your Linux partition resides.

hmm maybe I that was a typo, not sure. anyway I repeated with hd0,4 and getting the same unrecognized device string error

as for the uuid in grub 
pressing -e the uuid is already there

i can boot into windows but not into ubuntu 
:confused:

---

### Post by Elfy on 2008-12-21
I know the uuid is there but the line is saying root - it has to say uuid and then follow with the uuid.


```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
[COLOR="Red"]uuid[/COLOR]		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
```

---

### Post by logos34 on 2008-12-21
> **forestpixie said:**
> I know the uuid is there but the line is saying root - it has to say uuid and then follow with the uuid.


```
title		Debian GNU/Linux, kernel 2.6.27-11-generic
[COLOR="Red"]uuid[/COLOR]		ac46354f-2da9-4f31-9358-3b15b46d8175
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ac46354f-2da9-4f31-9358-3b15b46d8175 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
```

+1 

I wonder how many more of these errors we're going to see with kernel updates

---

### Post by mano cazalet on 2008-12-21
that worked

thanks a lot

---

### Post by Elfy on 2008-12-21
> **logos34 said:**
> +1 

I wonder how many more of these errors we're going to see with kernel updates

I don't even know when it changed to be honest - I just happened it notice it last time I was fiddling :)

---

### Post by logos34 on 2008-12-21
> **forestpixie said:**
> I don't even know when it changed to be honest - I just happened it notice it last time I was fiddling :)

I thought it changed with the release of 8.10...I kind of wished they had left it as 'root' because at least you could tell what partition # / was on.

---

### Post by Elfy on 2008-12-21
I thought maybe then as well.

The problem of course now is that people search and find all the similar threads - none of which will say anything about UUIDs or running blkid - so we'll get lots of fdisk -l that are now of no use :(

Still maybe they'll find this one :D

---

