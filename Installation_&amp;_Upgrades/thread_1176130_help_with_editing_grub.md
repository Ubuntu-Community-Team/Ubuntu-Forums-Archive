---
title: "help with editing grub"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by aughen on 2009-06-02
hi i have read the forms and help sites but i cannot get grub to load windows 7 i highlight it from the menu and press enter and nothing happens here is my stuff





aughen@aughen-desktop:~$ sudo fdisk -lu
[sudo] password for aughen: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44874486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x50365132

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    77031674    38515806   83  Linux
/dev/sdb2        77031675    80405324     1686825    5  Extended
/dev/sdb5        77031738    80405324     1686793+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58c114d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   312576704   156288321    7  HPFS/NTFS

[COLOR=Red]Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa35e1517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   160833535    80415744    7  HPFS/NTFS
aughen@aughen-desktop:~$ [/COLOR]
 

windows 7 is in red








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
default        5

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
## hiddenmenu

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
# kopt=root=UUID=1bf194a0-308f-4084-bb5b-6c36e0797488 ro

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
# howmany=4

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=1bf194a0-308f-4084-bb5b-6c36e0797488 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=1bf194a0-308f-4084-bb5b-6c36e0797488 ro single
initrd        /boot/initrd.img-2.6.24-24-generic


title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

[COLOR=Red]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows 7 
root        (hd2,0) 
makeactive 
chainloader    +1 [/COLOR]



don't know what i am doing wrong please help

---

### Post by logos34 on 2009-06-02
if the XP entry works, it means windows 7 is on either the 2nd or 4th disk, i.e. (hd1,0) or (hd3,0). Try those (remember the matching 'map' lines).  

BUT if you installed it AFTER XP, the* boot files* could be on the XP disk (hd2,0).  (I think--it does that when dual booting two windows on a *single* disk.)  Double-check XP boot.ini menu.

---

### Post by aughen on 2009-06-02
i installed windows 7 on a clean separate hard drive with no other drives hooked in to the motherboard because of a partition work around problem with the beta so i don't think that it crossed over to the win xp boot.ini

---

### Post by aughen on 2009-06-02
i tried that and it did not work but was interesting is when i was in grub and not the Ubuntu terminal i pushed "e" and the windows xp  came up as

[COLOR=DarkRed]root  (HD2,0)
savedefault
makeactive
map  (HD0) (HD2)
map  (HD2) (HD0)
chainloader +1
[/COLOR]
witch that looks right but when i went to the Windows 7 entry to the edit mode it looked like this


[COLOR=DarkRed]root  (HD1.,0)makeactivechainloader +1[/COLOR]


is it a problem that it is all in one line? and not separated like windows xp?


Thanks 

Justin

---

### Post by aughen on 2009-06-02
i got the issue resolved thanks for everyones time

the red didn't work but the black did do not know why excepted the spaces by the title????? weird



[COLOR=Red]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows 7 
root        (hd2,0) 
makeactive 
chainloader    +1 [/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows 7 
root (hd2,0)
makeactive
chainloader +1

---

### Post by aughen on 2009-06-02
sorry spaceing did not show up

---

### Post by aughen on 2009-06-02
ok well that fixed windows 7 but now when i go to xp it loads windows 7

---

### Post by aughen on 2009-06-02
the 250GB IS WINDOWS XP and the 160gb is storage and the 41.1gb id ubuntu and the 82.3 is WINDOWS 7 ... i just dont get it errr......

---

### Post by logos34 on 2009-06-02
> **aughen said:**
> i got the issue resolved thanks for everyones time

the red didn't work but the black did do not know why excepted the spaces by the title????? weird



[COLOR=Red]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows 7 
root        (hd2,0) 
makeactive 
chainloader    +1 [/COLOR]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows 7 
root (hd2,0)
makeactive
chainloader +1

not sure what's going on with grub here, i.e. how you can boot either windows without the map lines (they're on [non-first hdd]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"))

Since XP is on (hd2,0), I would have thought either of these would work for win7:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows 7 
root (hd1,0) 
map (hd0) (hd1)     
map (hd1) (hd0)
makeactive 
chainloader +1

or

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title Microsoft Windows 7 
root (hd3,0) 
map (hd0) (hd3)     
map (hd3) (hd0)
makeactive 
chainloader +1

---

### Post by aughen on 2009-06-02
ok here is what i did i just put both those entries in the grub  and named them 1 and 3 and here is what happened the windows 7 worked for windows 7  (HD2.0) and the (HD1,0) did not work at all but the (hd3,0) worked for xp

so yey it works but i have not had this much trouble with grub ever i dont understand why the (hd2,0) work for xp to one point and then switched to windows 7 but htank you  for all your help 


justin

oh and i added map lines to windows 7 and it did not work so i took them off and it works just fine now go figure

---

### Post by logos34 on 2009-06-02
> **aughen said:**
> ok here is what i did i just put both those entries in the grub  and named them 1 and 3 and here is what happened the windows 7 worked for windows 7  (HD2.0) and the (HD1,0) did not work at all but the (hd3,0) worked for xp

so yey it works but i have not had this much trouble with grub ever i dont understand why the (hd2,0) work for xp to one point and then switched to windows 7 but htank you  for all your help 


justin

oh and i added map lines to windows 7 and it did not work so i took them off and it works just fine now go figure

yeah, pretty bizarre

---

