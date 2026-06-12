---
title: "Grub loader reset during todays update, no XP now"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Inspector Gadget on 2009-07-29
Unfortunately I managed to reset grub loader today and cannot remember how to edit it to find my other drive which has my XP on it, Help!!!

all advice gratefully received

gadget

---

### Post by presence1960 on 2009-07-29
from ubuntu run these commands in terminal and post the output back here:

```
sudo fdisk -l
``` that is a lowercase L

```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

---

### Post by Inspector Gadget on 2009-07-29
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60046   482319463+  83  Linux
/dev/sda2           60047       60801     6064537+   5  Extended
/dev/sda5           60047       60801     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd99ab30b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         492     3948512    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 37)
les@les-desktop:~$ 

hiddenmenu
default 0
timeout 3

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
# kopt=root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d3a99ae1-3422-49db-99b4-81f934aee4e3

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

title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro  single
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro  single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=d3a99ae1-3422-49db-99b4-81f934aee4e3 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-07-29
If windows is on sdb1, and you are booting from sda first, then add this to the end of menu.lst:

title windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Also, it appears that these statements mean grub will not appear unless you press Esc superfast!  You may wish to modify them, especially by placing a hashmark (#) in front of hiddenmenu, and changing the timeout to 3.

hiddenmenu
default 0
timeout 3

---

### Post by presence1960 on 2009-07-29
```
title		Microsoft Windows XP 
rootnoverify    (hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

add the above to the end of your menu.lst file if you are booting first from sda in BIOS.

```
title		Microsoft Windows XP 
rootnoverify    (hd0,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

if you are booting first from sdb in BIOS add this at the end of menu.lst

you can edit the menu.lst file by opening a terminal and running ```
gksu gedit /boot/grub/menu.lst
```

after adding the entry that applies to you click save then close the file and reboot to see if you can boot windows.

---

### Post by presence1960 on 2009-07-29
thanks merlin you beat me to the punch  :D :popcorn:

---

### Post by merlinus on 2009-07-29
Yeah, but twice is nice!

BTW, if the OP is booting from sdb, does he need the map statements?

---

### Post by presence1960 on 2009-07-29
> **merlinus said:**
> Yeah, but twice is nice!

BTW, if the OP is booting from sdb, does he need the map statements?

No, i knew i forgot to edit something after pasting..lol

---

### Post by Inspector Gadget on 2009-07-29
Thanks guys, sorted !!

---

### Post by merlinus on 2009-07-29
Glad to hear it.  Have fun!

---

### Post by presence1960 on 2009-07-29
Enjoy Ubuntu!

---

