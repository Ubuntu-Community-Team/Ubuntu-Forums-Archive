---
title: "GRUB Error 2 on trying to boot LFS"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by krzysz00 on 2009-03-19
I recently installed LFS to /dev/sda7 Ubuntu boots fine, but if I try to boot LFS I get an error 2
/boot/grub/menu.lst
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=4dd96f1a-456a-4f28-a4ac-11846c41f075 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=vga=0x317

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4dd96f1a-456a-4f28-a4ac-11846c41f075 ro vga=0x317 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4dd96f1a-456a-4f28-a4ac-11846c41f075 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=4dd96f1a-456a-4f28-a4ac-11846c41f075 ro vga=0x317 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=4dd96f1a-456a-4f28-a4ac-11846c41f075 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title LFS SVN-20090316
root (hd0,6)
kernel /boot/lfskernel-2.6.28.7 root=/dev/sda7 vga=788

```sudo fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda4            1314       60801   477837360    5  Extended
/dev/sda5            3011       60477   461603677+  83  Linux
/dev/sda6           60478       60801     2602498+  82  Linux swap / Solaris
/dev/sda7            1314        3010    13631089+  83  Linux

Partition table entries are not in disk order

```Please help!

---

### Post by krzysz00 on 2009-03-19
Actually it's an error 17

---

### Post by krzysz00 on 2009-03-19
bump

---

### Post by meierfra. on 2009-03-19
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by krzysz00 on 2009-03-19
Here it is.

---

### Post by krzysz00 on 2009-03-20
Since I just booted this morning the exact error message is
> Error 2: Bad file or directory type

---

### Post by krzysz00 on 2009-03-20
Apparently it's the 256 inode problem. Any fixes? (OK, maybe should switch to grub 2?

---

### Post by meierfra. on 2009-03-20
The intrepid grub should handle 256 inodes just fine. Did you upgrade from previous version?

Try this


```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda
```

---

