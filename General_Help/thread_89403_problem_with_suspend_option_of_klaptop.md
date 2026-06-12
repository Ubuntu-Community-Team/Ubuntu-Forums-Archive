---
title: "problem with suspend option of klaptop"
date: 2005-11-12
forum: General Help
---

### Post by frankabel on 2005-11-12
Hi all!
When I test the "suspend" options on pop-up menu of KLaptop dons't work. Nevertheless the pop-up menu option "standby" work fine. My computer is Acer laptop TravelMate 520 and I have installed Kubuntu 5.10 Breezy.
Any idea?
Thanks in advance

---

### Post by daller on 2005-11-21
Correct me if I'm wring, but my experience is that most linux-laptops suffers from bad suspend-ability.

See this:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)

---

### Post by wabble on 2005-11-22
[QUOTE=frankabel]Hi all!
When I test the "suspend" options on pop-up menu of KLaptop dons't work. Nevertheless the pop-up menu option "standby" work fine. My computer is Acer laptop TravelMate 520 and I have installed Kubuntu 5.10 Breezy.
Any idea?
Thanks in advance[/QUOTE]

Maybe this can help you?

After Breezy i had to remove the nifty graphics on boot - splash - from the line noaltoptions and remove all comments to "vga=xxx" where xxx is the boot option you have added under install or later in menu.lst (so if you havent added a vga option this will not be there and you don't have to think about it).

Well here is what i do to get suspend2 up and running again.. (when hibernation crashes on resume)

sudo vim /boot/grub/menu.lst

locate the line

kopt=root=dev/hda1 ro

make sure there is no mentioning of [ vga= ], if there is. Remove it.

Then move further down and locate the line 

noaltoptions=quiet splash

Remove the word splash.

Save the file and then type in 

sudo grub-update

Vim is my editor of choice here. You can use whatever editor you like.

Not sure if this is what you where thinking of..

---

### Post by daller on 2005-11-23
[QUOTE=wabble]Maybe this can help you?

After Breezy i had to remove the nifty graphics on boot - splash - from the line noaltoptions and remove all comments to "vga=xxx" where xxx is the boot option you have added under install or later in menu.lst (so if you havent added a vga option this will not be there and you don't have to think about it).[/QUOTE]

Have you filled a bugreport on this?

...It's definately a bug if it has anything to do with the splash or vga-options...

I'll try your solution on my own laptop, and see where it gets me...

Thanks!

---

### Post by daller on 2005-11-24
[QUOTE=wabble]Maybe this can help you?

After Breezy i had to remove the nifty graphics on boot - splash - from the line noaltoptions and remove all comments to "vga=xxx" where xxx is the boot option you have added under install or later in menu.lst (so if you havent added a vga option this will not be there and you don't have to think about it).

Well here is what i do to get suspend2 up and running again.. (when hibernation crashes on resume)

sudo vim /boot/grub/menu.lst

locate the line

kopt=root=dev/hda1 ro

make sure there is no mentioning of [ vga= ], if there is. Remove it.

Then move further down and locate the line 

noaltoptions=quiet splash

Remove the word splash.

Save the file and then type in 

sudo grub-update

Vim is my editor of choice here. You can use whatever editor you like.

Not sure if this is what you where thinking of..[/QUOTE]

I did what you described, but it doesn't work on my Dell Inspiron 8600


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro vga=0x31b nolapic quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro vga=0x31b nolapic single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, kernel 2.6.12-8-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hda1 ro vga=0x31b nolapic quiet splash
initrd          /boot/initrd.img-2.6.12-8-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hda1 ro vga=0x31b nolapic single
initrd          /boot/initrd.img-2.6.12-8-386
boot

title           Ubuntu, kernel 2.6.12-7-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-7-386 root=/dev/hda1 ro vga=0x31b nolapic quiet splash
initrd          /boot/initrd.img-2.6.12-7-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-7-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-7-386 root=/dev/hda1 ro vga=0x31b nolapic single
initrd          /boot/initrd.img-2.6.12-7-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


```

I've heard of a "nolapic" option, but is it relevant, and where should it be placed?

---

