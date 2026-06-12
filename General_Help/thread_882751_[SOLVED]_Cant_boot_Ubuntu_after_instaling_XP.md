---
title: "[SOLVED] Cant boot Ubuntu after instaling XP"
date: 2008-08-07
forum: General Help
---

### Post by SplasHmdfc on 2008-08-07
HI
So here is my problem:
I had windows xp and i installed Ubuntu and everything was great i love linux now but my xp got f*cked and i need to reinstall it so i did un reinstallation and now i cant boot my linux before when i turn on my pc it asked me whitch OS i whant and now it doesnt it just go and boot my f.ckin xp. 
Any ideas.. thx

---

### Post by Elfy on 2008-08-07
You need to reinstall grub is all - you can use your livecd or get supergrub - the info is all on here

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by SplasHmdfc on 2008-08-07
thanks

---

### Post by sayakb on 2008-08-07
Please mark the thread as solved. (Thread tools->Mark thread as solved)

---

### Post by SplasHmdfc on 2008-08-07
i woud but i still have a question ive installed grub and now it shows me the boot table but when i select Ubuntu i get the msg " Cannot Mount Partition" and i thing this is becous ive bugged my hd by using partition magic but ikd some sugestions shoud i reinstall ubuntu /??

---

### Post by caljohnsmith on 2008-08-07
SplasHmdfc, boot up a Live CD, and try the following:
```
sudo fdisk -l
```
That will tell you all your partitions, and look for the one that says "Linux" under the "system" category. Once you know that partition, mount it and print out Grub's menu.lst file:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Also, do the following:
```
sudo blkid
```
And then copy/paste the results back here for all those commands so we can help you further.

---

### Post by SplasHmdfc on 2008-08-07
ok so i type the fdisk -l and i get 

ubuntu@ubuntu:~$ sudo fdisk -l
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e721e72

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/hda2             639        9729    73023457+   5  Extended
/dev/hda5             639        4792    33366973+   7  HPFS/NTFS
/dev/hda6            4793        5116     2602498+   7  HPFS/NTFS
/dev/hda7            5117        8793    29535471    7  HPFS/NTFS
/dev/hda8            8794        9682     7140861   83  Linux
/dev/hda9            9683        9727      361431   82  Linux swap / Solaris
/dev/hda10           9728        9729       16033+  14  Hidden FAT16 <32M

```
then i type the other two commands 
```

ubuntu@ubuntu:~$ sudo mount /dev/hda8 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=db626eac-611a-4363-bd25-026d1e48b71e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$ sudo blkid
/dev/hda1: UUID="709C093B9C08FCFA" LABEL="Windows" TYPE="ntfs" 
/dev/hda5: UUID="70C41811C417D7E4" LABEL="Fun" TYPE="ntfs" 
/dev/hda6: UUID="F238E75638E717FD" LABEL="Programs" TYPE="ntfs" 
/dev/hda7: UUID="0F0B01F1D8B22CE1" LABEL="Filmi" TYPE="ntfs" 
/dev/hda8: UUID="db626eac-611a-4363-bd25-026d1e48b71e" TYPE="ext3" 
/dev/hda9: TYPE="swap" 
/dev/hda10: SEC_TYPE="msdos" LABEL="OSselector^G" UUID="DDC1-D7C1" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

```
thats it so now what ?

---

### Post by caljohnsmith on 2008-08-07
According to your fdisk output, it appears that Ubuntu is on /dev/sda8, which is (hd0,7) in Grub's World. Therefore, in all the Ubuntu entries in your menu.lst, change the
```
root (hd0,6)
```
to
```
root (hd0,7)
```
That should fix your booting problems if you don't have any additional issues.

---

### Post by SplasHmdfc on 2008-08-07
ok thanks for all ill post the resouts

---

### Post by SplasHmdfc on 2008-08-07
YEEE ty a lot it worked im with ubuntu now gr8

---

### Post by SplasHmdfc on 2008-08-07
woohow sry for the flood

---

