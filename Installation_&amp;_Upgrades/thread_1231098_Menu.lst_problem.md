---
title: "Menu.lst problem"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by olympic on 2009-08-04
Ubuntu 9.04, ACER Aspire 3630, 1Gb RAM, 160Gb HDD, dual boot Ubuntu / WinXP.

Just ran update manager and installed kernel 
Ubuntu 9.04, kernel 2.6.28-14-generic.

On reboot, this kernel did not appear in my boot options.  Both previous kernels (-11-generic and -13-generic), plus WinXP were there.

Did some chasing through the forums and found a thread which advised removing the existing "menu.lst" and running update-grub, which writes a new "menu.lst" file.

This worked in that it updated "menu.lst" to the latest two kernels (-13-generic and -14-generic)  BUT  it deleted the entry for WinXP.

I have manually added the entry for WinXp as it appeared in the "menu.lstBU" however when I now boot, my boot menu options list does not appear and my laptop boots straight into Ubuntu without the option to boot into WinXP.

Below is a copy of current "menu.lst"  

[I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=2400b199-5616-402d-926a-b41f858a2e99 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2400b199-5616-402d-926a-b41f858a2e99

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
uuid		2400b199-5616-402d-926a-b41f858a2e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2400b199-5616-402d-926a-b41f858a2e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		2400b199-5616-402d-926a-b41f858a2e99
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2400b199-5616-402d-926a-b41f858a2e99 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		2400b199-5616-402d-926a-b41f858a2e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2400b199-5616-402d-926a-b41f858a2e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		2400b199-5616-402d-926a-b41f858a2e99
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2400b199-5616-402d-926a-b41f858a2e99 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		2400b199-5616-402d-926a-b41f858a2e99
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
makeactive
chainloader	+1[/I]

---

### Post by drs305 on 2009-08-04
> **olympic said:**
> 

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]# [/COLOR]**hiddenmenu



Comment out (add a # symbol) at the start of the "hiddenmenu" line so the menu is displayed.

The timeout is currently set to 3, which will give you 3 seconds to halt the autologon to Ubuntu. If you want to adjust the timeout, change the value in "timeout  3"

---

### Post by olympic on 2009-08-04
Tks DRS305

All is now okay.:D
Do you know if grub update removes that hash from the "hidemenu" option automatically when you do an update?  Strange that my earlier update from -11 to -13 went without any problems.

If it wasn't for a word game called "Wordslinger" I would not have worried about not accessing WinXp.

---

### Post by drs305 on 2009-08-04
> **olympic said:**
> Tks DRS305
All is now okay.:D
Do you know if grub update removes that hash from the "hidemenu" option automatically when you do an update?  Strange that my earlier update from -11 to -13 went without any problems.

I ran the command in a Jaunty and Hardy VM and the "hiddenmenu" option did not change when I ran update-grub. I ran it with "hiddenmenu" commented and then uncommented and it remained as set in both cases.

---

### Post by presence1960 on 2009-08-04
when I upgraded to a newer kernel during the installation process of the upgrade a window opened asking whether i wanted to keep my old version of menu.lst or use the package managers version. Maybe this could be the source of your problem.

---

