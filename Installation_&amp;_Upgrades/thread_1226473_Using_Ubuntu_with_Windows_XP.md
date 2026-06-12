---
title: "Using Ubuntu with Windows XP"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by bemar on 2009-07-29
Hello,

I have a Windows XP installation on my PC with the following harddrive constellation. (Sorry its German)
"Datenträger 0" is my first drive with Windows XP SP3 and "Datenträger 2" is my Ubuntu drive. The first installation was my windows installation a long time ago. Today I've installed Ubuntu on "Datenträger 2" (SATA). But Ubuntu didn't modified the MBR so for default Windows is starting. I've read that the Ubuntu installer should recognize the Windows installation and creating a Grub menu automaticly.
Then I've tried to start Ubuntu by using the Boot Menu of my BIOS to select the harddrive to boot from but I only get "Error 17" at the GRUB console. 

So currently I don't know where to start.

Thanks for your help.

Ben

[IMG]http://www.bemar.de/images/screenshot.jpg[/IMG]

---

### Post by bemar on 2009-07-29
Here are some additional informations from ubuntu side (LiveCD)
```

ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xa30c3bbf

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       30401   121314847+   7  HPFS/NTFS

Platte /dev/sdb: 82.3 GByte, 82348277760 Byte
255 Köpfe, 63 Sektoren/Spuren, 10011 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x1062a67e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1        9598    77095903+  83  Linux
/dev/sdb2            9599       10011     3317422+   5  Erweiterte
/dev/sdb5            9599       10011     3317391   82  Linux Swap / Solaris

Platte /dev/sdc: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00027601

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdc2           16709       19457    22081342+   7  HPFS/NTFS


```

So it seems the harddrives are in different order.
devices.map
```

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

```

menu.lst
```

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            d3d81c39-2975-4394-98eb-dbccb0a5583b
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=d3d81c39-2975-4394-98eb-dbccb0a5583b ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            d3d81c39-2975-4394-98eb-dbccb0a5583b
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=d3d81c39-2975-4394-98eb-dbccb0a5583b ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            d3d81c39-2975-4394-98eb-dbccb0a5583b
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Home Edition
rootnoverify    (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

---

### Post by presence1960 on 2009-07-29
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd2,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd2,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR of hd0, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

As long as you are booting from sda this will work.

---

### Post by merlinus on 2009-07-29
Try this whilst running from the live cd:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

---

