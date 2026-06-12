---
title: "&quot;Error 11 : Device string was not found&quot; ubuntu won't boot up"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by ashour on 2009-09-25
Hi,

i just did a fresh installation of ubuntu jaunty , i got windows Vista already installed , now whenever i try to boot into ubuntu it shows :
Error 11: Device string was not found

But windows vista boots ok

anyhelp with that?

---

### Post by rreese6 on 2009-09-25
Boot up with the LiveCD
fdisk -l to get the list of drives.
find the /dev/sbaX that linux is on
then cd /media/sbaX (X = the Number IE sba1)
then cd /boot/grub
ls -l
open menu.lst with sudo gedit menu.lst
post data here (fdisk and Menu.edit)

---

### Post by ashour on 2009-09-26
The content of menu.lst

but it was strange how i accessed it i found that for drive to be accessed its called "/media/disk-1" although "fdisk-l" showed that ext4 file system is on media sda3 

```

default 4
timeout 10

title Ubuntu 9.04, kernel 2.6.28-11-generic
root 
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c2628af7-f429-4587-ab12-16d61a97ada8 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root 
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c2628af7-f429-4587-ab12-16d61a97ada8 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
root 
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Windows Vista (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=c2628af7-f429-4587-ab12-16d61a97ada8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c2628af7-f429-4587-ab12-16d61a97ada8

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

```

fdisk output 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdac2a47a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6081    48839680    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            6081       12161    48839680    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           12162       18240    48829567+  83  Linux
/dev/sda4           18241       30402    97677312    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

couldn't find menu.edit did u mean menu.lst its already posted at the begining.

---

### Post by shredder12 on 2009-09-26
Error 11 occurs when a device string was exepcted and either it was not entered or it is invalid..

so i think.. you should give the device partition after root

so do the following change in your menu.lst file..

```

title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=c2628af7-f429-4587-ab12-16d61a97ada8 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

```

the change is (hd0,2) in front of the "root" command..

do this change save your file and reboot.. see if you are able to access now..

**btw create a backup of your menu.lst file before modifying it.**

---

