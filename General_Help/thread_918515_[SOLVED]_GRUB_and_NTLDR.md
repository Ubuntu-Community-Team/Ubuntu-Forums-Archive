---
title: "[SOLVED] GRUB and NTLDR"
date: 2008-09-13
forum: General Help
---

### Post by loaba on 2008-09-13
Hello everyone, need some help with a minor issue.

I have a dual-boot system with Ubuntu on one HDD and XP on a different HDD. GRUB sees the XP installation, but when I select it I get a message saying "NTLDR missing".

This isn't a major problem, it's more of a convenience issue. I can select the XP drive to boot first in BIOS and that works fine. How do I install NTLDR and where?

Thanks in advance.

---

### Post by cdtech on 2008-09-13
If you can boot your Window's drive through BIOS then its probably just a simple configuration issue within the "/boot/grub/menu.lst".

Could you post the output from:
```
gedit /boot/grub/menu.lst
```
This will give us a starting point.

**Update::.**
I use the same boot scheme and this is my menu.lst (Windows section).
```
title		Windows Vista
root		(hd1,0)
savedefault
chainloader	+1
```

---

### Post by loaba on 2008-09-13
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
default         0

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
# kopt=root=UUID=10700a54-ce2a-4c43-8678-214307e37a85 ro

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
##      altoptions=(single-user) single
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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=10700a54-ce2a-4c43-8678-214307e37a85 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=10700a54-ce2a-4c43-8678-214307e37a85 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=10700a54-ce2a-4c43-8678-214307e37a85 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=10700a54-ce2a-4c43-8678-214307e37a85 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by cdtech on 2008-09-13
Make a backup of your menu.lst (sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak) then try changing the last entry to this:
```
title Microsoft Windows XP Professional
root (**hd1**,0)
savedefault
chainloader +1
```
Set your BIOS to boot the Ubuntu drive first then try selecting the Windows from the menu list.

---

### Post by loaba on 2008-09-13
Hmm, won't let me save the edited file...

---

### Post by loaba on 2008-09-13
Ahh, I get it - I have to logon as root

---

### Post by cdtech on 2008-09-13
Sorry, Use "**sudo** gedit /boot/grub/menu.lst"

---

### Post by loaba on 2008-09-13
No go...

I believe this is correct (have to check BIOS to be sure)

Channel 0 - PATA (XP)

Channel 2 - SATA (Ubuntu)

Channel 3 - SATA

Therefore, I should use this
```
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
chainloader +1
```

---

### Post by cdtech on 2008-09-13
You are correct, I have my primary drive as my Ubuntu and my Vista as my secondary.

---

### Post by loaba on 2008-09-13
Well, thought I was correct

error message "no such partition exists"

so, is this right then?

```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
chainloader +1
```

BTW - thank you sir, the help thus far is much appreciated

---

### Post by loaba on 2008-09-13
Still no go

---

### Post by caljohnsmith on 2008-09-13
Loaba, to boot Windows XP from a HDD other than the HDD that is first in the boot order, you have trick Windows XP into thinking that it is actually on the boot HDD. That is what those "map" lines are for in your original Windows entry, so you definitely need them. Cdtech may not need the mapping lines since he is booting Vista, not XP, but is actually new to me as I thought Vista required the same mapping trick. Your original syntax should be correct:
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
The fact that you get a "ntldr is missing" error and not a Grub error means that Grub has successfully booted Windows, but the problem might be with your BIOS settings (or something else) since you said Windows can boot successfully if its HDD is booted first on start up. Are your HDDs a mixture of IDE and SATA maybe? Also, please post the output of:
```
sudo fdisk -lu
```

---

### Post by loaba on 2008-09-13
Cal - yes, I am running a legacy PATA drive along with two other SATA drives. I may just be easier to reinstall XP on the second SATA and go from there.


```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97eb5bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390700799   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb1bf2efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   154191869    77095903+  83  Linux
/dev/sdb2       154191870   160826714     3317422+   5  Extended
/dev/sdb5       154191933   160826714     3317391   82  Linux swap / Solaris

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
16 heads, 63 sectors/track, 159560 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdbc24aad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   160833455    80416696+   7  HPFS/NTFS
```

---

### Post by caljohnsmith on 2008-09-13
Try the following in your menu.lst, as using (hd2) is probably just the wrong HDD:
```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
On start up, Grub sees the order of drives the same as the BIOS boot order, which may not be the order of drives given in /dev in Ubuntu; thus there is ambiguity as to which sdX drive corresponds to (hdY). So give the above a shot, let me know how it goes, and also let me know of any errors you might get.

---

### Post by loaba on 2008-09-13
That worked, Windows boots as it should. I wonder what is the cause of the syntax mix up.

---

