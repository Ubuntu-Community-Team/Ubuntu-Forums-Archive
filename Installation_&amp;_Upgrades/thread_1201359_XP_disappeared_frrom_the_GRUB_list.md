---
title: "XP disappeared frrom the GRUB list"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by sobingt on 2009-07-01
my name is sobin and i am an ubuntu beginner.i am facing a problem to boot into my windows XP as it disappeared from my GRUB list.

this is the result of sudo fdisk -l

--------------------------------------------------------------------------------------------------------------------

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12477   100221471    7  HPFS/NTFS
/dev/sda2           12478       13693     9767520   83  Linux
/dev/sda3           13694       14593     7229250   82  Linux swap / Solari


------------------------------------------------------------------------------------------------------------------------

and this is the result of gksudo gedit /boot/grub/menu.lst

--------------------------------------------------------------------------------------------------------------------------
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
# kopt=root=UUID=cfe3c937-c593-4247-8c73-6964c40a055b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cfe3c937-c593-4247-8c73-6964c40a055b

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
uuid        cfe3c937-c593-4247-8c73-6964c40a055b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cfe3c937-c593-4247-8c73-6964c40a055b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        cfe3c937-c593-4247-8c73-6964c40a055b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cfe3c937-c593-4247-8c73-6964c40a055b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        cfe3c937-c593-4247-8c73-6964c40a055b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



----------------------------------------------------------------------------------------------------------------------------


i tried adding 

title Windows XP
root (hd0,0)
chainloader +1

after ### END DEBIAN AUTOMAGIC KERNELS LIST ---but then again when the GRUB list boots to Ubuntu platform when i enter Windows XP in the list.

waiting to be helped......

---

### Post by tommcd on 2009-07-01
Try changing your entry for XP in menu.lst to this:
```

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
Were you ever able to boot into XP after installing Ubuntu?
I assume you are using grub 0.97 and not the new grub2, is that correct? Grub 0.97 is the one you get with a default Ubuntu 9.04 install.

And welcome to the Ubuntu forums!

---

### Post by sobingt on 2009-07-01
thanks tommcd but that doesn't work ....while i installed Ububtu for the ist time ,everything was fine i booted in windows xp and ubuntu.....then came an error while starting the laptop.

GRUB loading......
Error 17:


and i couldnot boot to either Ubuntu nor windows....So i reinstalled Ubuntu again which solved the problem and again one day the same error and the same solution solved it.After 4 th time of reinstallation of ubuntu,the Xp disappeared from the list.i have no clue what to do...

And i want to add one more thing this may be silly but when the system starts,it cames like

Grub loading stage 1.5......
Press Enter for the menu 0

but when i enter windows XP in the list(which came after entering 
title Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1     )


Grub loading stage 2......
Press Enter for the menu 0

---

### Post by sobingt on 2009-07-01
" **I assume you are using grub 0.97 and not the new grub2, is that correct? Grub 0.97 is the one you get with a default Ubuntu 9.04 install. **"
                                                                                        
                                                                                           ---tommcd
how to find which is my grub version???

---

### Post by tommcd on 2009-07-01
> **sobingt said:**
> 
                                                                  
how to find which is my grub version???
If you don't know what grub you have, if you did not deliberately install grub2, then you have grub 0.97. So don't worry about that.

I don't know why you keep getting grub error 17. You should not need to constantly reinstall Ubuntu like you have been doing.
Try using a Super Grub Disc:
[http://members.iinet.net/~herman546/SuperGrubDiskPage.html](http://members.iinet.net/~herman546/SuperGrubDiskPage.html)
...and see if this fixes you Windows boot problems.

If that doesn't work, see this thread about BIOS settings:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

If that does not help, then boot your Windows XP install CD and fix the MBR:
[http://ubuntuforums.org/showthread.php?t=381839](http://ubuntuforums.org/showthread.php?t=381839)
Then you will need to reinstall grub to the MBR like this from the live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
Hopefully you should be able to boot either XP or Ubuntu after this.

---

