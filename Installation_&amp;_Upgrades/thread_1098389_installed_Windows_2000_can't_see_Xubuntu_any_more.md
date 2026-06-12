---
title: "installed Windows 2000 can't see Xubuntu any more"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by sansa dude on 2009-03-17
ok i had Xubuntu on my computer on a 40gb for my laptop. i used an ubuntu live cd and cut that down to 18gb so i have 2 partitions with about 18gb in them one if for xubuntu the other is NTFS.

When i went to the windows 2000 set up i saw my NTFS partition and went to install there and now all it boots up is windows 2000 i think i need to now re install the GRUB bootloader. so how would i go about fixing this?

---

### Post by Partyboi2 on 2009-03-17
You can boot the xubuntu disk at follow [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub.

---

### Post by sansa dude on 2009-03-17
ok i ran the grub which ran good and comes up but it won't see Windows 2000 now what can i do?

---

### Post by Partyboi2 on 2009-03-17
You may need to add Windows to your grub menu.lst. Can you open a terminal and post the output to
```
sudo fdisk -l
``` and
```
cat /boot/grub/menu.lst
```

---

### Post by sansa dude on 2009-03-17
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe671e671

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2414    19390423+  83  Linux
/dev/sda2            4772        4864      747022+   5  Extended
/dev/sda3   *        2415        4771    18932602+   7  HPFS/NTFS
/dev/sda5            4772        4864      746991   82  Linux swap / Solaris


that was from the first one

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=a17b4ed7-89b8-4a25-868e-2b050615b5dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a17b4ed7-89b8-4a25-868e-2b050615b5dd

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a17b4ed7-89b8-4a25-868e-2b050615b5dd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17b4ed7-89b8-4a25-868e-2b050615b5dd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a17b4ed7-89b8-4a25-868e-2b050615b5dd
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a17b4ed7-89b8-4a25-868e-2b050615b5dd ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a17b4ed7-89b8-4a25-868e-2b050615b5dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17b4ed7-89b8-4a25-868e-2b050615b5dd ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a17b4ed7-89b8-4a25-868e-2b050615b5dd
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a17b4ed7-89b8-4a25-868e-2b050615b5dd ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a17b4ed7-89b8-4a25-868e-2b050615b5dd
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



then it spat all of that out for the 2nd one my windows 2000 is in the NTFS one so how do I add that to the GRUB list?

---

### Post by sansa dude on 2009-03-17
any ideas?

---

### Post by GenePayne on 2009-03-17
Try this:

Save a copy of your GRUB menu file first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then open the file for editing:
```
sudo gedit /boot/grub/menu.lst
```

Paste the following at the end of the file:
```
title           Microsoft Windows 2000
root            (hd0,2)
savedefault
makeactive
chainloader     +1
```

---

### Post by sansa dude on 2009-03-17
no the 2nd command didnt work. it said 

```
sudo: gedit: command not found
```

then i ran 

```
gedit /boot/grub/menu.lst
```

then it told me to install gedit so i did
next i ran 

```
gedit /boot/grub/menu.lst
``` 

again added the line to the end of the file and it said i do not have permission to save the file. so do i need to some how be in root?

---

### Post by GenePayne on 2009-03-18
Yes, you need to have root permission to edit the file, that's why you add the sudo at the beginning of the line:
```
sudo gedit /boot/grub/menu.lst
```

From your previous post it sounds like you now have gedit installed. So if you type this, it should open the file, let you add the lines, and then allow you to save the file.

After saving, reboot and see if the bootloader has the option to boot into windows.

---

### Post by sansa dude on 2009-03-18
ok thanks it works! thanks for all the help!

---

