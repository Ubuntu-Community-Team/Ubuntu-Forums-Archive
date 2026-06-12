---
title: "Grub"
date: 2008-10-13
forum: General Help
---

### Post by Uchiha_madara on 2008-10-13
how can I retrieve the Grub menu after installing windows xp??
i forgot it??

---

### Post by krazykookmany on 2008-10-13
//

---

### Post by bodhi.zazen on 2008-10-13
It is quite easy 

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Elfy on 2008-10-13
> **Uchiha_madara said:**
> how can I retrieve the Grub menu after installing windows xp??
i forgot it??

Do you mean you've reinstalled windows and lost grub? If that si the case - reboot with the buntu livecd and reinstall grub with it.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

---

### Post by Uchiha_madara on 2008-10-13
> **forestpixie said:**
> Do you mean you've reinstalled windows and lost grub? If that si the case - reboot with the buntu livecd and reinstall grub with it.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

thanks a lot that what i was need

---

### Post by xandrogm on 2008-10-13
I have a similar problem. I installed ubuntu first. then windows. 
However, after recovering grub with the above-mentioned method I get grub error 17. 
I basically have the first area of my disk for windows (sda1, hd0,0), then a swap area (sda2, hd0,1) and finally my ubuntu partition (sda3, hd0,2).
with a live cd i can view the menu.lst file on sda3 but i can't save the changes to get grub to work properly because i don't have the permissions.
so now i have neither xp or ubuntu, could anyone give me a hand?

---

### Post by caljohnsmith on 2008-10-13
> **xandrogm said:**
> I have a similar problem. I installed ubuntu first. then windows. 
However, after recovering grub with the above-mentioned method I get grub error 17. 
I basically have the first area of my disk for windows (sda1, hd0,0), then a swap area (sda2, hd0,1) and finally my ubuntu partition (sda3, hd0,2).
with a live cd i can view the menu.lst file on sda3 but i can't save the changes to get grub to work properly because i don't have the permissions.
so now i have neither xp or ubuntu, could anyone give me a hand?
Are you getting the Grub error 17 before you see the Grub menu on start up or after you get the menu and select Ubuntu to boot? It sounds like yours is the latter case, and if it is, all you need to do is modify your menu.lst like you allude to. You can modify it with:
```
gksudo gedit /boot/grub/menu.lst
```
If you need help with it, please post the output of:
```
sudo fdisk -lu 
```
And also your menu.lst.

---

### Post by xandrogm on 2008-10-13
I get the error message before the menuand right after the loading count-down.can i use the "gksudo gedit /boot/grub/menu.lst" ion the grub command-line? 

```
ubuntu@ubuntu:~$ sudo fdisk -lu 
 
Disk /dev/sda: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x02c686dc 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   469997639   234998788+   7  HPFS/NTFS 
/dev/sda2       469997640   472391324     1196842+  82  Linux swap / Solaris 
/dev/sda3       472391325   488392064     8000370   83  Linux 
```





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
# kopt=root=UUID=305556ab-ea8a-40b5-87f9-e437d90a754a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=305556ab-ea8a-40b5-87f9-e437d90a754a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=305556ab-ea8a-40b5-87f9-e437d90a754a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=305556ab-ea8a-40b5-87f9-e437d90a754a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=305556ab-ea8a-40b5-87f9-e437d90a754a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

thank you

---

### Post by caljohnsmith on 2008-10-13
OK, from your Live CD, do the following:
```
sudo mount /dev/sda3 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
That should pull up your menu.lst. Then change the line that says "hiddenmenu" to:
```
#hiddenmenu
```
And also change all the Ubuntu entries to use:
```
root (hd0,2)
```
Instead of (hd0,1). And lastly, change the "#groot=(hd0,1)" to:
```
#groot=(hd0,2)
```
Save, reboot, cross your fingers, and let me know what happens. :)

---

### Post by xandrogm on 2008-10-13
> **caljohnsmith said:**
> 
Save, reboot, cross your fingers, and let me know what happens. :)

Well looks like everything works perfectly, XP, ubuntu, everything! Thank you so much! I was starting to think i'd have to reinstall ubuntu again or something painfully slow like that.
:guitar:

---

### Post by caljohnsmith on 2008-10-13
I'm glad you can boot all your OSes now and glad to help out; cheers and have fun Ubuntu-ing. :)

---

