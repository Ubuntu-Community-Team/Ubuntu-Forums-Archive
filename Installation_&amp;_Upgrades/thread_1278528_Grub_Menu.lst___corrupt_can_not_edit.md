---
title: "Grub Menu.lst   corrupt can not edit"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by robbieo11 on 2009-09-29
I have search and search tried about all.
i am currently on a live usb stick trying to get menu.lst corrected it is missing windows xp, windows reload partition and all ubuntu kernels including memtest86. this all happened after kernel update this am.

This is a Msi u100 wind  netbook 

below is containts of  menu.lst located in linux/boot/grub folder

"# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=9751b5a0-d523-4c83-a7dd-e81205e00d8f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9751b5a0-d523-4c83-a7dd-e81205e00d8f

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
# savedefault=false"


[COLOR="DarkOrange"]in terminal on usb "live" disk i type  sudo fdisk -l i get[/COLOR][/COLOR][/COLOR] 
[COLOR="DarkRed"]
"[COLOR="Sienna"]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac7ee453

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         510     4096543+  12  Compaq diagnostics
/dev/sda2             511        5610    40965750    7  HPFS/NTFS
/dev/sda3            5611        8797    25599577+   5  Extended
/dev/sda4            8798       19131    83007855    7  HPFS/NTFS
/dev/sda5            5611        8659    24491061   83  Linux
/dev/sda6            8660        8797     1108453+  82  Linux swap / Solaris

Disk /dev/sdb: 1009 MB, 1009778688 bytes
32 heads, 61 sectors/track, 1010 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     1651315     1777688   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(1651314, 30, 24)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(1777687, 27, 34)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      221758      619137   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(221757, 23, 51)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(619136, 23, 61)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957768     1940980   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(957767, 22, 38)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(1940979, 26, 37)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      540404      544668     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(540403, 13, 8)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(544667, 9, 17)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 512 MB, 512229376 bytes
16 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      784412     1935127   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(784411, 3, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1935126, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      170050     2121692   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(170049, 14, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2121691, 4, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?     1884962     3836603   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1884961, 2, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3836602, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?           1     3666559  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(3666558, 15, 30)
Partition 4 does not end on cylinder boundary.
[/COLOR]
Partition table entries are not in disk order[/COLOR]

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WINRE" UUID="FC86-1E8C" TYPE="vfat" 
/dev/sda2: UUID="BC5CAEDB5CAE8FA6" LABEL="OS_Install" TYPE="ntfs" 
/dev/sda5: UUID="9751b5a0-d523-4c83-a7dd-e81205e00d8f" TYPE="ext3" 
/dev/sda6: UUID="82de335f-bdca-49b5-9ec7-9f242ca416cb" TYPE="swap" 
/dev/sdb: SEC_TYPE="msdos" LABEL="Pivot" UUID="0A62-70BB" TYPE="vfat" 
/dev/sdc: SEC_TYPE="msdos" UUID="B05C-C6E7" TYPE="vfat"  "



I tried to edit by doing sudo grub in teminal 
and doing the following


find /boot/grub/stage1returns with hd0,4
root (hd0,4)
setup (hd,0) 
then quit and reboot
but when i reboot i get the grub prompt  grub>    with no os choices

what can i do to repair this short of reloading drive 
thanks
rob

---

### Post by robbieo11 on 2009-09-29
noone can  help  what if i where to instal a 2nd ubuntu on drive with partion would that fix it??

---

### Post by robbieo11 on 2009-09-29
wow not one reply other than mine

---

### Post by leclerc65 on 2009-09-29
If you have another working computer, download Super Grub , burn it to a CD then try to fix the problem. Good luck.

---

### Post by drs305 on 2009-09-29
+1 on SuperGrub. It should get you back working. 

If you want to try to salvage what you have (Linux), you can try to rebuild your menu.lst.  It assumes sda was your primary partition and the one with Linux and Windows on it. I don't dual boot, but you could add a windows entry in after the linux one. The windows entry may or may not be correct.

You have no entries in the menu.lst you posted. I've posted a generic menu.lst but you will need to fill in the bold areas with the information for your system.

```
[noparse]
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
[/noparse]

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9751b5a0-d523-4c83-a7dd-e81205e00d8f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9751b5a0-d523-4c83-a7dd-e81205e00d8f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false"
## ## End Default Options ##

title		Linux
root		(hd0,4)
kernel		/boot/vmlinuz-**2.6.24-24-generic** root=UUID=9751b5a0-d523-4c83-a7dd-e81205e00d8f ro quiet splash
initrd		/boot/initrd.img-**2.6.24-24-generic**
quiet

title		Windows 
rootnoverify	(hd0,1)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

You seem to have access to you system - are you using a LiveCD. If so, mount your / partition (sda5):
```

sudo mkdir /mnt/temp
sudo mount /dev/sda5 /mnt/temp
ls /mnt/temp/boot | grep "vmlinuz"

```
This should return the available kernels: 
vmlinuz-**2.6.31-11-generic**

Choose one, replace the bold section of menu.lst to match, save and reboot.
```

gksudo gedit /mnt/temp/boot/grub/menu.lst

```

We can repair menu.lst and get the rest back once you can boot into your system.

---

### Post by robbieo11 on 2009-09-30
:popcorn:ended up moving fies after small instal of ubuntu  yes triple boot  saved files to flash drive restarted in windows xp (with new install i also opted to install new bootloader)

in xp i deleted the partions with ubuntu on them so know i had to reinstall ubuntu 1 last time to have the os and correct bootloader

what a PITA not hard just redundant:popcorn:

---

