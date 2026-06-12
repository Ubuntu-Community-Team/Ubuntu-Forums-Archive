---
title: "GRUB Rebuilding?"
date: 2008-08-30
forum: General Help
---

### Post by Gailen on 2008-08-30
Hi, I have a Windows Vista + Ubuntu dual-boot computer. GRUB worked fine, but when I decided to format Vista and install XP, as expected, GRUB was erased by MBR. Well, I restored the GRUB using Super Grub Disc, but it keeps restoring the old GRUB: Windows Vista/longhorn appears.

I wonder if there is a terminal command in ubuntu t rebuild correctly the GRUB

Thanks

---

### Post by caljohnsmith on 2008-08-30
Super Grub Disk gave you Grub back by reinstalling Grub to your HDD's master boot record (MBR). But Super Grub Disk did not change your Grub's /boot/grub/menu.lst, which has your Windows entry. So if you can boot into Ubuntu, open a terminal, and please post the output of the following commands:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Then we can easily modify your menu.lst for your new Win XP entry.

---

### Post by VMC on 2008-08-30
Go here for a brief document on how to recover Grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Gailen on 2008-08-31
OKay, this is what I get from the first command

```
Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xbf766238

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048    20973567    10485760   27  Desconocido
/dev/sda2        20980890   174160664    76589887+   7  HPFS/NTFS
/dev/sda3       174176255   255610214    40716980    f  W95 Ext'd (LBA)
/dev/sda4       255612928   425480183    84933628    7  HPFS/NTFS
/dev/sda5       174176256   216119295    20971520   83  Linux
/dev/sda6       216121344   220315647     2097152   82  Linux swap / Solaris
/dev/sda7       220315662   255610214    17647276+  83  Linux

``` 
(I'm using the Spanish version)

This is from the second. I've erased the # entries.

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=26e70578-32e2-49ac-8b8b-0c3f625063db ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=26e70578-32e2-49ac-8b8b-0c3f625063db ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Thanks for your help.

---

### Post by caljohnsmith on 2008-08-31
It looks like Windows XP is on either sda2 or maybe sda4, and my guess would be sda2. Try modifying your menu.lst, so first do:
```
gksudo gedit /boot/grub/menu.lst
```
And then change the Windows entry at the bottom of that file as follows:
```
title          Windows XP
root		[COLOR="Blue"](hd0,1)[/COLOR]
savedefault
makeactive
chainloader	+1

```
Save changes, reboot, and see if that works. If not, change (hd0,1) above to be (hd0,3) and that should work. Let me know how it goes and if you have any problems.

---

### Post by Gailen on 2008-08-31
Yes, it worked.

Thank you very much

---

