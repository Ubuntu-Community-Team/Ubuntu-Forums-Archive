---
title: "Error message when I open &quot;Startup Manager&quot;"
date: 2008-08-02
forum: General Help
---

### Post by explorer716 on 2008-08-02
I get this error message every time I open "Startup Manager"

Your grub configuration file lacks the line "### END DEBIAN
 AUTOMAGIC KERNELS LIST".
You have probably hand-edited the configuration file.

Choose "yes" to have the file auto-generated. This means that any custom boot options will be lost.
If you only have one operating system installed and you do not know what I am talking about, it should be safe to answer "yes".

Otherwise, choose "no". That will stop this program.
It is however recommended to look into this, since system upgrades could also rewrite the configuration file.

I take the corrective action suggested, but I still get the error message the next time I open "Startup Manager".

You help will be appreciated.

---

### Post by drs305 on 2008-08-02
If you post the results of this command we can help you restore your grub menu.lst:
```
cat /boot/grub/menu.lst
```

---

### Post by explorer716 on 2008-08-02
This is the results from the, "cat /boot/grub/menu.1" command.


robert@robert-desktop:~$ cat /boot/grub/menu.1st" command
default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 all_generic_ide
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=795

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

robert@robert-desktop:~$

---

### Post by drs305 on 2008-08-02
Make a backup of your menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-old
```

Open menu.lst for editing:Replace the entire contents with this (use whatever text editor you want):
```
gksu gedit /boot/grub/menu.lst
```

Replace the entire contents with this:
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
##### hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd1,0)/boot/grub/splashimages/fiesta.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 all_generic_ide
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=50dac002-bd7b-496c-9cb6-11fb35dd3ab4 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

### END DEBIAN AUTOMAGIC KERNELS LIST


```

I recommend using StartUp-Manager to edit the grub settings you need to make in the future. A link to the tutorial on how to install and run it is in my signature. It's an excellent app and allows you to safely tweak lots of grub settings.

---

### Post by explorer716 on 2008-08-02
Thank you very much!!  Your recommendation fixed the problem.  Thanks again.:):):)

---

### Post by Beanmonster on 2008-08-11
I would really like to change my Usplash and WDM theme again, but this time Startup-Manager will not load.

The "Performing pre-configuration tasks" dialog pops up and after 3 seconds it just exits.

I have tried reinstalling SUM but to no avail.

The above helped a bit but it still does not load.

I have had problems with menu.lst before (accidentally deleted it) but recovered it.

Any advice?

---

### Post by Beanmonster on 2008-08-12
I solved the problem!!! 

Turns out grub.cfg did not exist.

All I had to do was copy menu.lst in the /boot/grub folder and rename it grub.cfg.

Hooray!!!:guitar:

---

