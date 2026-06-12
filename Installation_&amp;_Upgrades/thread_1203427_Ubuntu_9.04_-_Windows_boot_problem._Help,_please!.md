---
title: "Ubuntu 9.04 - Windows boot problem. Help, please!"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by angeldorado on 2009-07-03
Hi! I'm new linux user. I have both Ubuntu and Windows Xp installed in my computer. I updated to Ubuntu last version and now I'm not able to boot my windows because I don't have that option in boot menu anymore. What can I do? Thank you.

---

### Post by merlinus on 2009-07-03
Enter these commands one at a time in a terminal, and post results:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

BTW, did you upgrade or do a fresth install, and to which version of ubuntu?

---

### Post by lindsay7 on 2009-07-03
Are you able to boot into Ubuntu and do you get the grub menu when you start the computer showing the boot options?

Merlinus, I just your your post... I am going to watch and learn.

---

### Post by angeldorado on 2009-07-03
[B]Yes I did an upgrade.
Before[/B] the upgrade I used to get 3 options in the boot menu:
*1)* Ubuntu <don't remember>, kernel <don't remember> -generic
*2)* Ubuntu <don't remember>, kernel <don't remember> -generic (recovery mode)
*3)* Windows Xp Profesional
**After** upgrading to 9.04 I get these 5 options:
1) Ubuntu 9.04, kernel 2.6.28-13-generic
2) Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
3) Ubuntu 9.04, kernel 2.6.27-7-generic
4) Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
5) Ubuntu 9.04, memtest86+
**NO WINDOWS :(**[U][B]

Firs Command[/B][/U] (sudo fdisk -l)

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfafbfafb

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       38913   158971207+   5  Extendida
/dev/sda5           19123       38104   152472883+  83  Linux
/dev/sda6           38105       38913     6498261   82  Linux swap / Solaris

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf3cdf3cd

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1      121600   976751968+   7  HPFS/NTFS

_**Second Command**_ (cat /boot/grub/menu.lst)_**:**_

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
default        2

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
# kopt=root=UUID=57d07769-dc49-4c1a-ae01-0642dc10ee42 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=57d07769-dc49-4c1a-ae01-0642dc10ee42

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        57d07769-dc49-4c1a-ae01-0642dc10ee42
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=57d07769-dc49-4c1a-ae01-0642dc10ee42 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        57d07769-dc49-4c1a-ae01-0642dc10ee42
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=57d07769-dc49-4c1a-ae01-0642dc10ee42 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        57d07769-dc49-4c1a-ae01-0642dc10ee42
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=57d07769-dc49-4c1a-ae01-0642dc10ee42 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        57d07769-dc49-4c1a-ae01-0642dc10ee42
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=57d07769-dc49-4c1a-ae01-0642dc10ee42 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        57d07769-dc49-4c1a-ae01-0642dc10ee42
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-07-03
Add this to the very end of menu.lst:

title windows
rootnoverify (hd0,0)
makeactive
chainloader +1

and restart.

---

### Post by angeldorado on 2009-07-03
> **lindsay7 said:**
> Are you able to boot into Ubuntu and do you get the grub menu when you start the computer showing the boot options?

Merlinus, I just your your post... I am going to watch and learn.

Yes, Ubuntu boots and works fine. But no windows-start option. ](*,) I don't know what "grub menu" is, sorry I'm (very) new.

---

### Post by angeldorado on 2009-07-03
> **merlinus said:**
> Add this to the very end of menu.lst:

title windows
rootnoverify (hd0,0)
makeactive
chainloader +1

and restart.

And... How exactly can I do that? I mean.. where? That "menu.lst" is a file? Pardon me, but I'm like 2 hours linux user.

---

### Post by merlinus on 2009-07-03
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by natravis on 2009-07-03
> **angeldorado said:**
> And... How exactly can I do that? I mean.. where? That "menu.lst" is a file? Pardon me, but I'm like 2 hours linux user.

Press Alt+F2 and then type in the command that Merlinus said. It will bring up a text editor. Add the info he posted to the end of the file, save it, then reboot and it should be there.

---

### Post by angeldorado on 2009-07-03
:mrgreen: NOW is OK! Problem solved! Thank you, Merlin!!

---

### Post by merlinus on 2009-07-03
Excellent news!  Welcome to the forums, and happy ubuntuing.

---

