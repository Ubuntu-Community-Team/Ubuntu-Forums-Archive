---
title: "Grub Error 21 and 22"
date: 2009-06-18
forum: Hardware
---

### Post by GilbertEvanG on 2009-06-18
Hello,
I've been having this weird problem that I have yet to resolve, so maybe someone can shed some light on this for me.

I have my new HP dv7t laptop set to dual boot (Vista came installed, and I installed Ubuntu onto the second partition/drive of my dual hard drive).

That part is working great. However, booting does not work so well if I have an external hard drive plugged in.

I have two external hard drives that I would like to have always plugged into my laptop. Right now, my computer will let me have one specific one plugged in on boot and it works fine. If the second external is plugged in during boot (whether it is the only one plugged in, or they are both plugged in) I get Grub Error 22.

There is a different issue if I choose to "Reboot" instead of "Shut Down". If I choose "Reboot", I get a different Grub error when the computer reboots, Error 21. If I manually power off the computer after Error 21 and then power it on again, it boots up fine (with the external still plugged in). This happens when I reboot from Vista or Ubuntu.

Some people have theorized that this is a bios problem where the computer is mounting the external hard drives before my internal drives, making the order different then what Grub is expecting. This makes sense, except in my bios there is no way to manage the external hard drives in the boot order. The only hard drive related device is "Internal Notebook Drive" or something like that. And it doesn't make much sense why I can have one external plugged in but not the other.

Does anyone have any ideas on how to resolve this?

Your help will be greatly appreciated. Thank you.

---

### Post by lindsay7 on 2009-06-18
Check your bios setting again. Usb devices sometimes are not considered hard drive. So the boot order should be 

1. cd/dvd
2. usb devices
3. hard drives

Note the #3 would have a priority for the hard drives i.e. hd0, hd1 etc.

The same could be true for #2 with usb1,usb2, etc.

---

### Post by GilbertEvanG on 2009-06-18
Ok I hit the escape button when my computer boots and it prompts me with a menu of a few choices.

The two relevant choices are:
F9 - Boot Device Options
F10 - BIOS Setup

When I hit F9 it shows me a list of the devices I have and I can pick which one to boot from. (This list does show both of my external hard drives on it).

When I hit F10, I then navigate to the "Boot Order" section, and here is the order:

1. Internal CD/DVD ROM Device
2. Notebook Hard Drive
3. USB CD/DVD ROM Device (not sure what this is)
4. USB Diskette on Key/USB Hard Disk (didn't notice this one before)
5. USB Floppy (not sure what this is)
6. Network Adapter

Based on that order, shouldn't it load my internal drives first?

(I also tried moving option 4 ahead of notebook hard drive, and I still got the same error 22 as before)

---

### Post by GilbertEvanG on 2009-06-18
Here is the contents of my menu.lst file.
This is the first time I have really used Linux before, so let me know if there is any other output that could help debug the situation.

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.l

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
timeout        30

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
# kopt=root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a1683c9-f892-4586-bad6-d5cdca60b251

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



## Custom Menu ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista Home Premium
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        
root

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (recovery)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd1,4)
kernel        /boot/memtest86+.bin
quiet


## ## End Default Options ##

##title        Ubuntu 9.04, kernel 2.6.28-11-generic
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
##initrd        /boot/initrd.img-2.6.28-11-generic
##quiet

##title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro  single
##initrd        /boot/initrd.img-2.6.28-11-generic

##title        Ubuntu 9.04, memtest86+
##uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
##kernel        /boot/memtest86+.bin
##quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
##title        Other operating systems:
##root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
##title        Windows Vista (loader)
##rootnoverify    (hd0,0)
##savedefault
##makeactive
##chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
##title        Windows Vista (loader)
##rootnoverify    (hd0,1)
##savedefault
##makeactive
##chainloader    +1

```

---

### Post by cariboo on 2009-06-18
You seem to have made quite a mess of /boot/grub/menu.lst

Instead of moving Vista to the top of the list, you just modify the boot order in this line:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

```

By changing the 0 to 5, Windows would boot by default. 

By using the device and partition, instead of uuid, you are now having problems when external drives are plugged in. I have have the same type of motherboard that changes the device labels on every boot, by using uuid the problem stopped.

Hopefully you backed up /boot/grub/menu.lst before making any changes. If you did I would suggest you use the backup and just change the default boot as show above.

---

### Post by GilbertEvanG on 2009-06-18
I forgot to mention something.

It started out by using UUIDs (if you look at the default options at the bottom that I commented out). And when it was doing that, I couldn't have any external hard drives plugged in at all (on boot).

By changing it to the hard drive partition (hd1,4) for some reason it let one of my external hard drives plugged in on boot (but not the other one).

Thanks for pointing out that default option thought, I missed that.

---

### Post by GilbertEvanG on 2009-06-18
Here's some more information:

I restored the backup copy of my original menu.lst file (uses UUID rather than a specific hard drive). The behavior is the same as it was with my modified version. It lets me have one certain external hard drive plugged in, but if I plug in the other one I get grub Error 22.

I then tried temporarily commenting out the windows stuff from my menu.lst file (since that too referenced a specific hard drive), so everything that was in the file only used UUID's, and the same behavior exists.

EDIT:
Here is my original menu.lst file that was created when I installed Ubuntu 9.04:
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
# kopt=root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a1683c9-f892-4586-bad6-d5cdca60b251

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3a1683c9-f892-4586-bad6-d5cdca60b251 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3a1683c9-f892-4586-bad6-d5cdca60b251
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by Hobgoblin on 2009-06-18
> **GilbertEvanG said:**
> 
1. Internal CD/DVD ROM Device
2. Notebook Hard Drive
3. USB CD/DVD ROM Device (not sure what this is)
4. USB Diskette on Key/USB Hard Disk (didn't notice this one before)
5. USB Floppy (not sure what this is)
6. Network Adapter


Can you set all but 1 and 2 to disabled?

Also is there another menu to set the order of hard drives used?

I have the same problem, in my case the BIOS will set the card reader on my printer as second HDD.  Which causes me a problem as Ubuntu is on there.

---

### Post by GilbertEvanG on 2009-06-18
It appears that all I can do is change the order of those 6 items unfortunately. I looked through the help on that menu and there was nothing mentioned about how to disable an option, just what keys to press to move them up or down.

EDIT:
On the menu before the boot order, there are options to disable the floppy boot, and network adapter (they already were disabled), as well as the CD/DVD ROM Drive. Nothing about the USB stuff.

---

