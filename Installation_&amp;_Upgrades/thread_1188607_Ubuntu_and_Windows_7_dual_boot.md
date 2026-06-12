---
title: "Ubuntu and Windows 7 dual boot?"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by benmandude on 2009-06-15
I just installed JJ and it won't let me boot in into win7. Here is what I did to get to this point.

I had xp and 7 dual booting, deleted the xp partition, formatted to ext3 installed ubuntu.

Ubuntu is booting fine but in the boot loader it shows me the ubuntu options and windows xp. i tried xp option shows missing hal.dll, im thinking it shows to a deleted xp install.

I tried my 7 disk to repair the startup and it isnt detecting the 7 install, so that is kind of dead end. I'm wondering if i can edit grub boot loader to point it to the 7 install but I don't know where to start.

---

### Post by merlinus on 2009-06-15
Open a terminal and post results of:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by benmandude on 2009-06-15
[FONT=monospace]Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d881d87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9572    76887058+   5  Extended
/dev/sda2            9573       18242    69634048    7  HPFS/NTFS
/dev/sda5               1         249     2000029+  82  Linux swap / Solaris
/dev/sda6             250        9572    74886966   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd509d509

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       32300   244187968+   7  HPFS/NTFS

[/FONT]

---

### Post by merlinus on 2009-06-15
Is windows on sdb1?  What about the second command output?

---

### Post by benmandude on 2009-06-15
sdb is my storage drive. I'm going to say 7 is on sda2. 

Here is the boot.lst, I just posted the non commented lines.
I see that it shows xp at the bottom but im not sure how to change it to the 7 partition.


-----------------------------------------
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5d3d8f7e-05d8-40fd-93aa-ce1adae71db3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d3d8f7e-05d8-40fd-93aa-ce1adae71db3 ro xforcevesa quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5d3d8f7e-05d8-40fd-93aa-ce1adae71db3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5d3d8f7e-05d8-40fd-93aa-ce1adae71db3 ro xforcevesa  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5d3d8f7e-05d8-40fd-93aa-ce1adae71db3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by merlinus on 2009-06-15
Use gparted and change the boot flag to sda2.

Also, change the windows entry in menu.lst to:

title        Microsoft Windows 7
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by benmandude on 2009-06-15
Some progress, when I choose win7 it gives me bootmgr missing. I'm going to run win7 disk and see if it can detect the os now.
 
EDIT: Success, repair detected and fixed the bootmgr. Working 100%. Thank you so much for your help merlinus

---

