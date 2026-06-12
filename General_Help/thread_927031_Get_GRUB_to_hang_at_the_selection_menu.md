---
title: "Get GRUB to hang at the selection menu?"
date: 2008-09-22
forum: General Help
---

### Post by Cindres on 2008-09-22
I've managed to get my 2 hard drive Vista/Ubuntu 8.04 dual booting running properly now, only one thing i want changing.

Currently when i turn my computer on, i have to sit and watch out for the black grub screen to come up, where it gives you a couple of seconds to hit escape and choose what to boot into (Normal Ubuntu, recovery mode, and of course for me Vista). 
I can boot Vista fine through this method, but what I'd like is to go straight to the selection screen and hang there until i pick which operating system i want to boot into, with me having to hit 'Esc' at the right moment.
Is there a way i can do this?

Thanks in advance.

---

### Post by Titan8990 on 2008-09-22
What you need to is edit /boot/grub/menu.lst.

**First backup you menu.lst file in case something goes wrong**

To do this give the following command:

cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

Now, lets have a look at menu.lst:

```
jordan@einstein:/boot/grub$ cat menu.lst
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro

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

title           Ubuntu 7.10, kernel 2.6.22-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-server root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-server root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro single
initrd          /boot/initrd.img-2.6.22-15-server

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=eb90ff26-b99d-44b3-aedc-f641b6ed6faa ro single
initrd          /boot/initrd.img-2.6.22-14-server

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


To edit this file: 


gksu gedit /boot/grub/menu.lst


To start in order to not have to hit ESC to get to the GRUB menu:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

We comment this line out by adding a "#" to the beginning like so:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Then you will no longer have to hit ESC to get the grub menu.

To prevent a timeout:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
```

We comment out the timeout line like so:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout         3
```


That should change grub to how you want it. Hope this helps.

---

### Post by Cindres on 2008-09-22
That's done the exact job.
Thanks a million!

---

### Post by Titan8990 on 2008-09-22
Good to hear. Don't forget to mark your topic as "solved" under "thread tools" at the top of the page.

---

