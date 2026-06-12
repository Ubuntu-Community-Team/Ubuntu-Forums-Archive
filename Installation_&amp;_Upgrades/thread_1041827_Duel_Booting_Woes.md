---
title: "Duel Booting Woes"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Token-Ring on 2009-01-17
The Problem:

I have Ubuntu on my first hard drive, and XP on my second. I installed XP first so that Ubuntu would over write the MBR with grub. All of that went fine, and I edited the menu.lst file to include XP. But when I select boot into XP from the grub menu all I see is "starting up..." and it just sits on that forever.


Here is my whole menu.lst file:

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
# kopt=root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP Pro
rootnoverify		(hd1,0)
makeactive
chainloader	+1



```

What do I need to change about my entry so XP will boot, or what else can I test to determine the problem?

-Thank you

---

### Post by 73ckn797 on 2009-01-17
> **Token-Ring said:**
> The Problem:

I have Ubuntu on my first hard drive, and XP on my second. I installed XP first so that Ubuntu would over write the MBR with grub. All of that went fine, and I edited the menu.lst file to include XP. But when I select boot into XP from the grub menu all I see is "starting up..." and it just sits on that forever.


Here is my whole menu.lst file:

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
# kopt=root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro

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

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=c2e31e4a-34d8-4f16-8ce6-2e5a760c56de ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP Pro
rootnoverify        (hd1,0)
makeactive
chainloader    +1



```What do I need to change about my entry so XP will boot, or what else can I test to determine the problem?

-Thank you


try adding "savedefault" and "map" info into the last entry of grub as follows:

```
title        Windows XP Pro
rootnoverify     (hd1,0)
map                (hd1,0) (hd0,0)
map                (hd0,0) (hd1,0)
savedefault
makeactive
chainloader    +1
```See what that does.

---

### Post by Token-Ring on 2009-01-17
Well I got farther With it this time. Now I see:

```
Starting up...

NTLDR is missing
Press Ctrl+Alt+Del to restart
```

I assume that this is a windows error and not a Ubuntu error, right? 

Any one know how to fix that?

---

### Post by Shazaam on 2009-01-17
You have the Ubuntu drive set up as the first boot device in your bios, correct? I am pretty sure the map entry has to be in sequence (someome correct me if I am wrong)...
```
# This entry automatically added by the Debian installer for a non-linux OS

title		Microsoft Windows XP Pro
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by Token-Ring on 2009-01-17
I still get the NTLDR is missing error, I googled it and it seems to be a windows error due to missing boot files. What I am not sure of is how to fix it and still maintain my duel booting.

---

### Post by Shazaam on 2009-01-17
This site may have an answer for you...
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_Booting_errors)

---

### Post by kranny on 2009-01-17
The first question that arises here is did you install Windows XP unplugging the first hadr drive(wid linux on it) or not?

btw the map command fools grub to map your xp drive.the problem for your error may be that grub isn't seeing those sata drives as hd0 and hd1. You can find out what grub sees in a grub console - this is available either at boot, by pressing the 'c' key, or if grub is not booting, from a linux live cd, use the command 'grub' or 'sudo grub'. Once you have a live cd, use TAB-autocompletion - type 'root (' then hit the TAB key, you should get a list of drives, as grub sees them.

---

### Post by 73ckn797 on 2009-01-17
> **kranny said:**
> The first question that arises here is did you install Windows XP unplugging the first hadr drive(wid linux on it) or not?

btw the map command fools grub to map your xp drive.the problem for your error may be that grub isn't seeing those sata drives as hd0 and hd1. You can find out what grub sees in a grub console - this is available either at boot, by pressing the 'c' key, or if grub is not booting, from a linux live cd, use the command 'grub' or 'sudo grub'. Once you have a live cd, use TAB-autocompletion - type 'root (' then hit the TAB key, you should get a list of drives, as grub sees them.


I have found that grub does not always read hard drive order like the bios does. You would have to possibly edit drive designation in grub as a way to discover what works as I have quoted here.

---

### Post by kranny on 2009-01-17
Point noted..

---

