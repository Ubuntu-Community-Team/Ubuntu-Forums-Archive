---
title: "Bad 7.10 Gutsy boot"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by s00n on 2007-10-14
I installed Ubuntu 7.10 Gutsy Gibbon a month ago. I've been installing the updates when they come out.

In the last big update, my visual effects simply don't work. I'm on "none" effects mode right now. 
Another thing that happens now is that, at the boot, the screen goes black and the loading screen doesn't appear. Then, I must press ctrl+alt+f1, and ctrl+alt+f8 to get back. After that, boot continue without the loading screen but in text mode. After that everything is fine. I login and here I am. But still, with now composition and no desktop effects.

Anyone knows how to solve this or at least has the same problem?

---

### Post by PmDematagoda on 2007-10-15
For the problem concerning your splash screen, type:-

```
sudo gedit /etc/boot/menu.lst
``` (lst with a simple L)

Post your menu.lst file and we can tell you what to do next about this.


About your desktop effects, what VGA card do you have?

---

### Post by s00n on 2007-10-15
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
# kopt=root=UUID=7b8fb088-0cdb-4fdd-ae94-567938e6f9e2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b8fb088-0cdb-4fdd-ae94-567938e6f9e2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b8fb088-0cdb-4fdd-ae94-567938e6f9e2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```

I have an ATI x700 pro 128mb. Thing is I didn't have any problem until the update i mentioned. I was running compiz-fusion and an emerald them plus awn dock. Everything was running smoothly and perfectly well. Then I did that update and never ran again. When I try to turn effects on it tells me that there was an error.

Tnx for your support.

---

### Post by buntunub on 2007-10-15
Hey welcome to the ever growing club of those who have display issues with Gutsy! I have a feeling that this release is going to probably be the most painful in Ubuntu history, but well see. They are certainly trying to push the envelope with that new integrated Displays and Graphics tool, so trying to fit everyone under one X display hat, kinda thing. For the longest time I could not even get the nvidia-settings tool to work with it because the native tool would always overwrite whatever changes the nvidia tool made to xorg.conf. At least starting from last Friday I was finally able to get my dual screens working (via nvidia-settings) and it hasnt been borked since... But it seems to me that the native tool and Nvidia cards just wont play nicely.

Edit: your menu.lst looks fine to me except maybe you have default 0 instead of savedefault. You have an ATI card I noticed, and ATI card linux drivers are in their infancy right now. ATI has said that for alot of cards the .40 driver wont do 3D yet, and the .41 still leaves alot to be desired. Check your xorg.conf and read the xorg guides here and elsewhere to get a handle on what your settings should be for your card.

---

### Post by s00n on 2007-10-15
But thing is I didn't had any problems! And on a reboot from an update some days ago it simply stopped working! I work perfectly with no effects but I was ok with them. Just wanted to know what happened lol.

---

### Post by PmDematagoda on 2007-10-16
As I have an Nvidia card I am afraid I cannot help you much, but about your splash screen, you can disable by editing the last part of the menu.lst file like this:-

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7b8fb088-0cdb-4fdd-ae94-567938e6f9e2 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
```

And see if that solves your problem.

---

### Post by s00n on 2007-10-16
I'll give it a try. Tnx.

---

### Post by s00n on 2007-10-16
Didn't work. Made a new update of 150mb now. Waiting for the final release to see some kind of solve to this. Tnx anyway.

---

### Post by PmDematagoda on 2007-10-16
Hmm, shall we try one last thing? Change that splash command to nosplash and see if that helps.

---

### Post by s00n on 2007-10-16
> **PmDematagoda said:**
> Hmm, shall we try one last thing? Change that splash command to nosplash and see if that helps.

It works m8. Tnx. Thing is i still don't have the loading screen. But don't have to press ctrl+alt+f1 and then back to ctrl+alt+f8.

Hope to get this fixed in the final version.

---

### Post by tombott on 2007-10-16
> **s00n said:**
> 
I have an ATI x700 pro 128mb. Thing is I didn't have any problem until the update i mentioned. I was running compiz-fusion and an emerald them plus awn dock. Everything was running smoothly and perfectly well. Then I did that update and never ran again. When I try to turn effects on it tells me that there was an error.

Tnx for your support.

I have the same card and the same problem.

Desktop / Visual Effects work on install, then after installing updates it no longer works.

---

