---
title: "broken partitiontable"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by denen.cyg on 2009-11-10
hi everyone... i've got the feeling that I have got a broken partition table.

here's my situation:
after installing latest latest jaunty kernels i did overwrite my /boot/grub/menu.lst with the maintainers -> reconfiguring menu.lst manually -> my xp partition did not boot anymore -> screen just showing "Starting up ..." no error messages  -> trying to recover mbr and part table with xp repair console -> fixmbr and fixboot are said to be successful -> bootcfg /rebuild unsuccessful due to "corrupt filesystem" -> chkdsk /r repair does finish successfully -> still no avail with bootcfg rebuild due to "corrupt filesystem" -> trying to reinstall grub via live cd -> grub> find /boot/grub/stage1 leads to "error 15: file not found"

here's my fdisk-l and sfdisk -d output:

```

320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb08ab08a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        4986    20515005    5  Extended
/dev/sda3            4987       10085    40957717+   7  HPFS/NTFS
/dev/sda4   *       10086       38913   231560910    7  HPFS/NTFS
/dev/sda5            2433        4864    19535008+  83  Linux
/dev/sda6            4865        4986      979933+  82  Linux swap / Solaris

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id=83
/dev/sda2 : start= 39070080, size= 41030010, Id= 5
/dev/sda3 : start= 80100090, size= 81915435, Id= 7
/dev/sda4 : start=162015525, size=463121820, Id= 7, bootable
/dev/sda5 : start= 39070143, size= 39070017, Id=83
/dev/sda6 : start= 78140223, size=  1959867, Id=82

```

am i assuming correctly that my partition table is broken? and if so... how can i fix this?

any help much appreciated!

update: I managed to restore grub with the following help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by MichealH on 2009-11-10
I have had a close look and I assume your Windows id dev/sda4 ?? can I see your /boot/grub/menu.lst file to see if thats broken.

---

### Post by denen.cyg on 2009-11-10
yes sda0,4

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
timeout		5

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
# kopt=root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=de022931-5d02-4770-9ff7-cd0382e4f1f5

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


title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,3)
chainloader +1

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		de022931-5d02-4770-9ff7-cd0382e4f1f5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=de022931-5d02-4770-9ff7-cd0382e4f1f5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

```

i've tried rootnoverify and makeactive aswell and hd0,3 and 0,4

---

### Post by MichealH on 2009-11-10
I saw in there:

Windows XP
sda3???

That could be your problem here could you change the 3 for a 4 and try again.

---

### Post by denen.cyg on 2009-11-10
i did so... using the very basic editor that grub provides at startup... i've been trying to fix this for hours now ... grr

---

### Post by MichealH on 2009-11-10
Do you have a Live CD at hand? If you do boot it and mount your disk (if it hasn't done already) then edit your list but if you don't have permissions open a terminal go to the file and type sudo chmod 777 menu.lst if u need help ask here on this thread.

---

### Post by denen.cyg on 2009-11-10
yes i do have a live cd at hand and its up and running atm. the problem is that grub is not installed anymore since i tried to fix it with xp's repairconsole (fixmbr). currently i am trying to get grub running again so i can at least use my jaunty inst. on sda2 edit: looks like it ain't 2 ... trying to work through this doc atm [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by MichealH on 2009-11-10
goto the terminal on the Live CD and type sudo apt-get install grub-pc and see what happens

---

### Post by denen.cyg on 2009-11-10
see first post for update!

now i am trying to fix that one partition xp is installed on... by reinstalling (that is installing win7) in the same place

---

### Post by denen.cyg on 2009-11-10
I am at a point where i am thinking of backing up all the not yet backed up data of that hd and repartitioning and reformatting the whole drive...

---

