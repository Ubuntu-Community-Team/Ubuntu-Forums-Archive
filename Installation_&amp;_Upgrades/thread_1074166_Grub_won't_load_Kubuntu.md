---
title: "Grub won't load Kubuntu"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Mindrage on 2009-02-18
Hi, I Installed Kubuntu 8.10 64-bit recently. It worked perfectly dual-booting with Windows Vista.
The Vista was installed first adn it replaced the Vista Boot Loader with GRUB.
But i wanted my vista boot-loader back so i installed EasyBCD and recovered the vista boot loader. Then i copied the GRUB boot-loading text and Installed NeoGRUB into the Vista Bootloader also... but now it can't find the Directory even if it was directly copied from the Kubuntu.
I tried to boot it from other partitions but it couldn't find it anywhere. So if anyone could tell me how to fix the Neogrub or just simply reinstall GRUB (first need to find out which partition it was installed on.)

Here is bootentry file:
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
# kopt=root=UUID=f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f92fbd09-1a2d-47a8-8ab9-f066bfc44ee9
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

Please, i really don't want to reinstall my vista again for it. ;)
Thanks and Cheers in advance :popcorn:

---

### Post by caljohnsmith on 2009-02-19
I would recommend reinstalling Grub to the MBR (Master Boot Record) and using that as your boot loader. You can do that from your Live CD by opening a terminal/konsole and doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Kubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how that goes or if you run into problems.

---

### Post by Mindrage on 2009-02-19
> **caljohnsmith said:**
> I would recommend reinstalling Grub to the MBR (Master Boot Record) and using that as your boot loader. You can do that from your Live CD by opening a terminal/konsole and doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Kubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how that goes or if you run into problems.

Thx alot it worked perfectly ;) but it seem to also have gotten my Windows Recovery HD also :P 
Could you tell me how to to access the bootentry so i can Rename them cause i can't tell the diffrense between some of them :/

---

### Post by caljohnsmith on 2009-02-19
Glad that worked OK. To change your menu.lst, while you are in Kubuntu do:
```
kdesu kate /boot/grub/menu.lst
```
And the first Vista entry near the bottom of that file that uses (hd0,0) is probably your Vista recovery partition. Most likely the Vista entry that uses (hd0,1) is the one you want to keep.

---

