---
title: "can 9.04 grub be edited by a newbie?"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Zaragon on 2009-04-29
I have Vista installed on my computer and just added desktop 9.04.  Ubuntu install was successful. Is there a way to edit GRUB that won't drive a newbie insane?  What I want to do is make Vista the default system to load.  This needs to be done to prevent my wife from killing me.  I welcome any suggestions.  Please don't point me at a Wiki article...I nearly drowned in unfamiliar terms when I tried that.

---

### Post by upchucky on 2009-04-29
to open a terminal click Applications > Accessories > Terminal

type this in the terminal 


```
 sudo gedit /boot/grub/menu.lst

```

then enter your administration password you created when you did the install.

this opens the menu.lst file that has the info to boot either operating systems

I modified mine and it is posted below for reference.

you can see the entry for windows at the very bottom, you can use the mouse to right click select the entire entry for windows, then copy and paste it above the first entry for ubuntu. 

you can put hash marks # in front of each line of the old windows entry at the bottom and the boot up will now ignore the old entry. or you can just delete the lines of the old entry

save the file and close. the next boot will boot windows first by default.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


title		Ubuntu 8.04, kernel 2.6.24-16-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd		/boot/initrd.img-2.6.24-16-386


title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux #OS
# on /dev/sda2
#title		Windows XP Media Center Edition
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1

```

---

### Post by Zaragon on 2009-04-29
Thanks Upchucky...I've printed your response to my question so that I can actually sit down and digest it.  It looks like just what I need.   Again, thanks

Zack

---

### Post by drs305 on 2009-04-29
If you would rather just change it via a menu, install StartUp-Manager. Everything you would need to know is in the link in my signature line. Learning to edit system files is a good thing, but there is a time and place for other methods too.

---

### Post by Herman on 2009-04-30
:) Did anyone notice the SIGN that's to warn you not to put foreign boot stanzas in the automagic kernels area?
> Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
The Debian Automagic Kernels list begins with these lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```The Debian Automagic Kernels list ends with this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

```If you put your Windows entry anywhere in between the beginning of the Debian Automagic Kernels list and the end of the Debian Automagic Kernels list, your Windows entry will be automagically deleted at every kernel update.

You can safely put your Windows entry *above* the Debian Automagic Kernels list if you like, or you can leave it below and edit the line for 'default', but it's really not a good idea to leave it inside the Debian Automagic Kernels list area.  :)
Example:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
[B]# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title        Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1


### BEGIN AUTOMAGIC KERNELS LIST[/B]   
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
# kopt=root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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


title        Ubuntu 8.04, kernel 2.6.24-16-386
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-386
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-386 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-16-386 root=UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 ro single
initrd        /boot/initrd.img-2.6.24-16-386


title        Ubuntu 8.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux #OS
# on /dev/sda2
#title        Windows XP Media Center Edition
#root        (hd0,1)
#savedefault
#makeactive
#chainloader    +1
```

---

### Post by upchucky on 2009-04-30
nice catch Herman, i hadn't even noticed.

as Herman pointed out the entry for windows should be before the automagic list, or after and then marked as default.

---

