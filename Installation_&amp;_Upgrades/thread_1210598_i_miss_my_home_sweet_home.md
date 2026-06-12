---
title: "i miss my home sweet home"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by gioz on 2009-07-11
hello,

actually i use ubuntu,

i wanted to try opensuse.

then installed opensuse on another part.

i can't see ubuntu from opensuse's grub.

my ubuntu : ext4 and 64bit.

take me home.

---

### Post by oldos2er on 2009-07-11
You can either add Ubuntu to Opensuse's grub menu, or restore Ubuntu's grub and add Opensuse to that.

---

### Post by SuperSonic4 on 2009-07-11
Since they're likely to use the same grub file just add ubuntu to Opensuse's. If you post out ```
sudo fdisk -l
``` and point out which one is ubuntu and ```
cat /boot/grub/menu.lst
``` it should enable someone to tell you how to do it

---

### Post by gioz on 2009-07-11
oh of course ;

actually as you can see my computer is alike tuesday bazaar. i have to access to ubuntu for my files. then i'll install   ubuntu clearly (only ubuntu). opensuse ? it's closed prison.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23d923d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15200   122093968+   7  HPFS/NTFS
/dev/sda2   *       15201       30401   122102032+   5  Extended
/dev/sda5           15201       15686     3903763+  82  Linux swap / Solaris
/dev/sda6           23107       30401    58597056    b  W95 FAT32
/dev/sda7           15687       18297    20972826   83  Linux
/dev/sda8           18298       23106    38628261   83  Linux

Partition table entries are not in disk order
``````
# Modified by YaST2. Last modification on Sat Jul 11 22:27:37 EEST 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.23-0.1
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.27.23-0.1-default root=/dev/disk/by-id/ata-ST3250410AS_6RY4ZRND-part7 resume=/dev/disk/by-id/ata-ST3250410AS_6RY4ZRND-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.23-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.23-0.1
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.27.23-0.1-default root=/dev/disk/by-id/ata-ST3250410AS_6RY4ZRND-part7 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.23-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1
```

---

### Post by gioz on 2009-07-11
i've installed ubuntu again. 

thanks.

sometimes new beginning is better.

ubuntu forever.

---

### Post by philcamlin on 2009-07-11
ah thats a bummer :(

---

