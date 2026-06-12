---
title: "&quot;RC Kernel&quot;"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by captcadaver on 2009-07-06
According to this article, some "RC kernel" exists that can make Ubuntu Netbook Remix run like awesome on my EEE 900:

[http://www.geekzone.co.nz/nzsouthernman/6494](http://www.geekzone.co.nz/nzsouthernman/6494)

How do I, uh... get this kernel?

---

### Post by coffeecat on 2009-07-06
The link to get the kernel is there in step 8! :p

Download the *apw5_i386.deb files for linux-image* and linux-headers*. That's two files. You can use the 'sudo dpkg -i *deb' terminal command if you want or simply double-click on the .deb files and let the graphical app gDebi install them for you.

By the way, this kernel does not make NBR "run like awesome". There is a bug in the regular kernel that makes mouseover on the NBR desktop very sluggish and awkward. This apw5 kernel simply fixes this bug.

---

### Post by captcadaver on 2009-07-06
:(

I spend money on a degree, yet I can't read...

Thanks much for your help, kind sir.

---

### Post by captcadaver on 2009-07-07
Ahh, I recently updated my system with everything the update manager suggested. It replaced my kernel and I'm back to lagginess.

I tried to do reinstall the RC kernel again. Despite having this kernel, I'm getting that icon lag again...

Thoughts?

---

### Post by coffeecat on 2009-07-08
I haven't used my Eee for some time, so I'm guessing what's going on here.

The special kernel is version 2.6.28-11, but the latest official kernel is 2.6.28-13 and that is what you're probably now booting into. Obviously, they still haven't fixed this issue. However, the 2.6.28-11 kernel should still be installed and should still be available from the grub menu.

If your grub menu is hidden, press esc shortly after you start up (you should see a prompt top left of screen) to reveal it. Then select the -11 kernel from the menu.

If you want the system to boot into the special -11 kernel as the default or have the grub menu show up at start up, you'll need to edit your /boot/grub/menu.lst file. Post back if you need any help with this.

**Edit:** just to confirm (or refute) my assumptions, please open a terminal and post the output of:

```
uname -r
```

That'll tell us which kernel you've booted into. While you're about it, post the contents of /boot/grub/menu.lst as well.

---

### Post by captcadaver on 2009-07-08
I never knew that was the GRUB menu did... cool. I went in and selected the correct KERNEL, and it runs nicely:

2.6.28-11-generic

So, what do I edit in this file?

---

### Post by captcadaver on 2009-07-08
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
# kopt=root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=90b566c1-4f83-44d1-8d24-4ddbe283236b

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by presence1960 on 2009-07-09
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default [COLOR="Red"]0[/COLOR]

change the red number to a 3.

---

### Post by coffeecat on 2009-07-09
> **presence1960 said:**
> change the red number to a 3.

Errr.. not quite! :wink: Don't forget that grub counts from 0, so to boot from the third menu entry as default, that line needs to be "default 2". If the OP sets it to 3, the system will boot into recovery mode as a default - which will be unfortunate. :|

**captcadaver**, you've got two options, both of which involve editing menu.lst, for which you need root privileges. To do this, open a terminal and...

```
gksudo gedit /boot/grub/menu.lst
```**Either**, change the default line to...

```
default 2
```**or** move the whole of the two -11 stanzas to above the -13 ones. What that means is that this lot:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic
```comes before this lot:

```
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        90b566c1-4f83-44d1-8d24-4ddbe283236b
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=90b566c1-4f83-44d1-8d24-4ddbe283236b ro  single
initrd        /boot/initrd.img-2.6.28-13-generic
```... which means that the first -11 option becomes the default if you leave the default line set to zero. Be aware though that whichever you choose the same problem will recur when and if a new-numbered kernel comes through the updates.

By the way - all those lines beginning with a hash (#) are commented lines. They are skipped when the system parses them. So, if you want the menu to appear when you boot up, simply put a # in front of the line "hiddenmenu".

---

### Post by captcadaver on 2009-07-09
I love you.

---

### Post by presence1960 on 2009-07-09
good catch coffeecat, I knew that but must have went braindead. I have 0 for my default...go figure!

---

