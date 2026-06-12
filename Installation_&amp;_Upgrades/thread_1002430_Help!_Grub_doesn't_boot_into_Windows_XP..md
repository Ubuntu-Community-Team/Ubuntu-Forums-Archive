---
title: "Help! Grub doesn't boot into Windows XP."
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by animeshb on 2008-12-05
I installed Windows XP on my HDD first and then I installed Ubuntu. Before starting the Ubuntu installation, in the Advanced GRUB options, I selected Windows XP Professional since I wanted XP as the default booting option. 

But when I reboot, XP isn't default option and also when I select it and press return, it says GRUB loading stage 2... and comes back to boot options

Here is my menu.lst

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
# kopt=root=UUID=fbc983f2-1918-48e5-963c-0d2fb77eed30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fbc983f2-1918-48e5-963c-0d2fb77eed30

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
uuid		fbc983f2-1918-48e5-963c-0d2fb77eed30
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fbc983f2-1918-48e5-963c-0d2fb77eed30 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		fbc983f2-1918-48e5-963c-0d2fb77eed30
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fbc983f2-1918-48e5-963c-0d2fb77eed30 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		fbc983f2-1918-48e5-963c-0d2fb77eed30
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
root		(hd0,0)
savedefault
chainloader	+1

------------------------------------------------------------------


I tried changing the default  0 option to 4, but it is still the same. 

Thanks,
animeshb.

---

### Post by animeshb on 2008-12-05
here is an output from gparted,
it shows the ntfs partition with a caution icon.
how do i make xp partition visible again.

please help.

[IMG]http://bayimg.com/image/gamhjaabe.jpg[/IMG]

---

### Post by chewearn on 2008-12-05
If I remembered correctly, the Advanced GRUB option of Ubuntu installer is to select where GRUB will be installed.  It is not for selecting which OS will be the default boot option.

My guess is, your WinXP bootloader has been overwritten by GRUB due to the misunderstanding above.  My suggestion is to:
1. run WinXP recovery (fixmbr), to fix booting into WinXP
2. then reinstall GRUB, and edit /boot/grub/menu.lst to fix boot order

---

### Post by animeshb on 2008-12-05
> **chewearn said:**
> If I remembered correctly, the Advanced GRUB option of Ubuntu installer is to select where GRUB will be installed.  It is not for selecting which OS will be the default boot option.


Oh, my curiousness has brought me into a big trouble then.

> **chewearn said:**
> 
My guess is, your WinXP bootloader has been overwritten by GRUB due to the misunderstanding above.  My suggestion is to:
1. run WinXP recovery (fixmbr), to fix booting into WinXP
2. then reinstall GRUB, and edit /boot/grub/menu.lst to fix boot order


So does it mean the ntfs partition is intact, but only inaccessible?

And could you please tell me in a more elaborate manner, as to how to use the fixmbr and how to reinstall the grub.

---

### Post by Nathan Sweeney on 2008-12-05
To run fixmbr, boot from a Windows XP install disc, at some point, you should be able to press "R" to boot into a recovery console.  Then you can run the fixmbr command.  Your linux install will not be bootable, as the XP bootloader (NTLDR) will run instead of grub.  Just run the Ubuntu Live cd and reinstall grub to get your linux partition bootable again.

---

### Post by animeshb on 2008-12-05
> **Nathan Sweeney said:**
> To run fixmbr, boot from a Windows XP install disc, at some point, you should be able to press "R" to boot into a recovery console.  Then you can run the fixmbr command.  Your linux install will not be bootable, as the XP bootloader (NTLDR) will run instead of grub.  Just run the Ubuntu Live cd and reinstall grub to get your linux partition bootable again.

Sorry for making this too long. So I should just run fixmbr? no options or attributes go with it?


I have the Ubuntu 8.10 iso burnt on a dvd. How do I reinstall grub from it? 

Thanks.

---

### Post by chewearn on 2008-12-05
> **animeshb said:**
> Sorry for making this too long. So I should just run fixmbr? no options or attributes go with it?

[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)


> I have the Ubuntu 8.10 iso burnt on a dvd. How do I reinstall grub from it? 

Thanks.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2008-12-05
I would not recommend running "fixmbr", because all that does is replace Grub in the MBR (Master Boot Record) with a Windows MBR so that you lose your dual boot and would boot straight into Windows *if* the Windows partition were OK; but since you accidentally told Grub to install to the boot sector of the Windows partition (using the "advanced" settings), your Windows partition is unfortunately not OK at present. :) I think what you really want to do is fix the Windows XP partition boot sector, not the MBR, and then you should be able to boot Windows just fine. If you have your Windows XP Install CD, you can do that with:
```
fixboot
```
If you don't have a Windows Install CD, let me know, and you can do the equivalent of the "fixboot" command using "testdisk" in Ubuntu. Let me know how it goes or if you run into problems.

---

