---
title: "Practical question about GRUB"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Xavier71 on 2009-06-04
Having installed a dual boot between Vista and Jaunty, I now have the following boot menu:

1 - Launch Ubuntu
2 - Launch Ubuntu in recovery mode
3 - Memtest
4 - Launch Vista
5 - Launch Vista

I have not too many issues for the top 3 but I find the last two entries disturbing.  I know where they come from (#4 is in fact the recovery drive of my laptop, #5 is the real Vista boot) but I also know that one day I will hit the incorrect one during boot time!!

So is there a way of making the boot menu just showing #1, #2 and #5, given that I'm unlikely to ever need the others...

And also, is it possible to swap the boot sequence so that Windows is default and not Ubuntu (at least for the time being).

Thanks

---

### Post by pastalavista on 2009-06-04
Download Startup Manager ```
sudo apt-get install startupmanager
``` and it makes it easy. You'll find it in the System > Administration menu after install. You could also do it by hand ```
gksu gedit /boot/grub/menu.lst
``` comment out (#) the items you don't want listed or make the whole menu hidden (hit escape to view) by uncommenting the appropriate line (#hidden menu). To manually make Vista default change the line 'default=0' to 'default=4'

---

### Post by x33a on 2009-06-04
+1 for pastalavista.

but just in case, post the output of
```
cat /boot/grub/menu.lst
```

---

### Post by Xavier71 on 2009-06-05
Job done thanks guys!  Here is the code, I don't think that there is any more issues with it.  I'm going to reboot and if it works I'll flag the post as solved.

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
default        4

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
# kopt=root=UUID=322a19ce-89d2-4781-af7d-ec01e2c6072e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=322a19ce-89d2-4781-af7d-ec01e2c6072e

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
uuid        322a19ce-89d2-4781-af7d-ec01e2c6072e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=322a19ce-89d2-4781-af7d-ec01e2c6072e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        322a19ce-89d2-4781-af7d-ec01e2c6072e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=322a19ce-89d2-4781-af7d-ec01e2c6072e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        322a19ce-89d2-4781-af7d-ec01e2c6072e
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Windows Vista (loader)
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1



```

---

### Post by Xavier71 on 2009-06-05
Mmmm, spoke a bit too soon.  I have only the 3 startup options I wanted, but Ubuntu is still the default!  I can live with that, but if you know what I have done wrong ....  Cheers

---

### Post by pastalavista on 2009-06-05
The default would have been 4 if you hadn't commented out those titles. Now it shoud be 2. The first title would be 0, the second 1 and the third 2.

---

