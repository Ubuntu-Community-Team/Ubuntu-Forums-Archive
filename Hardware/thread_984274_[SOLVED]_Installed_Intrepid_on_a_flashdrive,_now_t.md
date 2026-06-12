---
title: "[SOLVED] Installed Intrepid on a flashdrive, now trying to get my NTFS drive alive..."
date: 2008-11-16
forum: Hardware
---

### Post by Lupusceleri on 2008-11-16
Ok first of all, hello there, this would be my first post so forgive me for nab errors. And yes, I read the stickies first.

Now on to the real stuff. I have installed Intrepid Ibex (Xubuntu 8.10) to a flashdrive, a 16 GB Corsair Flash Voyager. The situation there is as follows:

- 4 or 5 GB (can't remember the exact value) primary partition, FAT32, so I can still plug it in on a Windows machine and use it as a "regular" USB-drive. The whole Linux part is like a double bottom in a suitcase there, all invisible to the windows machine. :D

- All the rest of the flashdrive is dedicated to Xubuntu, I let the installation pick the sizes of these partitions so I have no clue how much swap or ext3 I have.

- The bootloader is installed to the bootsector of the flashdrive. This means that I can plug out my flashdrive, and it will seem to my computer as if Xubuntu didn't exist at all. It also means I can plug it into another computer, reboot, and have my own files and stuff right there without having to modify the other computer in any way aside from maybe changing boot order.

Now I'm on my laptop, and trying to get access to its NTFS drive called "OS". And preferably making it mount to /media/C_Windows, on boot.

I have by now figured out this one is called "/dev/sda3". I've tried (and succeeded) to install ntfs-config, ntfsprogs. But if I, using NTFS-config, try to make it mount my /dev/sda3 it doesn't want to... At first I'd modified fstab using pysdm or something, it's called Storage Device Manager when installed. Then (I installed ntfs-config after I saw pysdm didn't work) NTFS-config gave me an error that it could not mount, and some blabber about going into windows and trying to unplug external devices which made me laugh because I did not run windows! The other option was forcing some stuff, but that looked scary so I didn't go there. :p

So I un-edited fstab, and rebooted, and tried NTFS-config again. Now it doesn't even *list* /dev/sda3, while it does list "RECOVERY" - /dev/sda2. And I have no idea why not! ;)

Because I know you guys love this command called sudo fdisk -l I'll include a dump from it - sorry but it is Dutch:

```
Schijf /dev/sda: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x60000000

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       14333   104547328    7  HPFS/NTFS
/dev/sda4           14333       14594     2097152    f  W95 Uitgeb. (LBA)
/dev/sda5           14333       14594     2096128   dd  [onbekend]

Schijf /dev/sdb: 16.1 GB, 16173236224 bytes
255 koppen, 63 sectoren/spoor, 1966 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x006154d5

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1         608     4883728+   c  W95 FAT32 (LBA)
/dev/sdb2             609        1966    10908135    5  Uitgebreid
/dev/sdb5             609        1902    10394023+  83  Linux
/dev/sdb6            1903        1966      514048+  82  Linux wisselgeheugen
```


Which leads me here - does anyone have any idea what on earth I'm doing wrong and how to fix it?

---

### Post by Lupusceleri on 2008-11-16
Ok I also figured out why my linux was so slow compared to when I used a regular live-USBstick... the stupid installation program made the swap partition only 500 MB, which is WAY too little from what I understand. So I tried to resize it to 2 GB which is the recommended size for my computer as said in one of the stickies, using Gparted. But that didn't work so I'll be reinstalling again, this time with a manual partition allocation! :)

I'll report back here with a fresh fdisk dump and if I still have the issue as soon as I can.

---

