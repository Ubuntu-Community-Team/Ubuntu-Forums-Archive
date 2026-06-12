---
title: "Stage2 grub looping"
date: 2009-05-09
forum: Hardware
---

### Post by fomorian on 2009-05-09
I have a single hard drive Dell laptop. I've been running Ubuntu for a little while but recently got an iphone and want to set up itunes to work with it. Rather than trying to work with wine and all that I figured I'd re-partition my hard drive and install windows xp. After much trail and tribulation I've got everything kind of working.

The problem I have now is when I select windows xp on the grub boot loader it reaches stage2 and will attempt to either load Ubuntu again or if I press esc I can try selecting windows xp again. It's basically a loop that I'm stuck in. Any insight would be greatly appreciated?

Below is the text from my menu.lst file.

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=10ebbf58-82a5-4126-93f3-759b854486af ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

title         Windows XP
root         (hd0,0)
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2009-05-09
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

