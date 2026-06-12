---
title: "[SOLVED] add windows to grub"
date: 2008-09-27
forum: General Help
---

### Post by KhaosMind on 2008-09-27
hi. i have some problems trying to boot windows from grub.

i have 2 disk. one sata 250gb with ubuntu. and the other is a 160 ide with two ntfs partitions in one, i installed windows on one and then restored grub following this [instructions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

my problem now is that grub doesn't detect windows and all my attempts to add it to menu.lst failed.

this is my fdisk -l output
 
```
sudo fdisk -l

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000d5f70

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        1305    10482381   83  Linux
/dev/sda2            1306       30270   232661362+  83  Linux
/dev/sda3   *       30271       30401     1052257+  82  Linux swap / Solaris

Disco /dev/sdb: 164.6 GB, 164696555520 bytes
255 cabezas, 63 sectores/pista, 20023 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x010f010f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdb2           16709       20022    26619705    f  W95 Ext'd (LBA)
/dev/sdb5           16709       20022    26619673+   7  HPFS/NTFS

```

to my undestanding windows is on /dev/sdb5 25gb partition

this is my menu.lst

```

# Pretty colours
#color cyan/blue white/blue

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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro

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
# howmany=1

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=17f89d16-2e3e-41d3-a5b4-d1efc6bd5334 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,4)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

i don't have any understanding of the whole master, slave thing so if that is a problem you should help me

the funny thing is that when i boot with the ubuntu live cd and select the option boot from the first drive, windows start.
but according the menu.lst the first drive is the one with ubuntu. and when i do find /boot/grub/stage1 from the live cd it says (hd1,0) but when i do it from my ubuntu instalation it says (hd0,0).
i dont know if this is relevant since i don't know anything about grub but i think it may be useful.
any other information, just ask for it.
anyway thanks for any help.

---

### Post by fooman on 2008-09-27
run this command in a terminal to edit grub using gedit:

```
gksudo gedit /boot/grub/menu.lst
```

change the xp entry to look like this:

```
title		Windows XP
root		(hd1,2)
makeactive
chainloader	+1
```

save the change and reboot.  see if you can boot into xp.  if not,  post back here with any error messages.

---

### Post by KhaosMind on 2008-09-27
sorry it doesn't work

error 22: No such partition.

any other idea?

---

### Post by fooman on 2008-09-27
> **KhaosMind said:**
> .

any other idea?

just one:

```

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

see if that one works.

---

### Post by kokkus on 2008-09-27
Here's how your menu.lst file should look like.
If you use WinXP Pro and not regular XP, just add it after Microsoft Windows XP.


default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1032646e-50c3-426a-8dff-e8ad2dca4d97 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Microsoft Windows XP 
root (hd0,0)
chainloader +1
savedefault
makeactive

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1032646e-50c3-426a-8dff-e8ad2dca4d97 ro single
initrd /boot/initrd.img-2.6.24-19-generic

---

### Post by KhaosMind on 2008-09-27
> **fooman said:**
> just one:

```

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

see if that one works.

it works, i cant believe it, cos i tried almost every number at first, i cant believe i didn't tried 0. there was a problem. when i put what you said it hanged up on starting. but thanks to [this]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/") i added 

title		Windows XP
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader	+1

now it works thank you very much. and sorry kokkus i read your post when the problem was already solved.

---

