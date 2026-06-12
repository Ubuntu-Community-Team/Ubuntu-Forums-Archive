---
title: "Windows won't boot after Ubuntu 8.10 Install"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Burette on 2008-12-07
This is a common problem but after reading most threads, I not smart enough to make it work on my own.

I have two physical hard drive
[LIST]
[*]a 160Gb
[*]a 640 Gb
[/LIST]

I wanted to have both WinXP and Ubuntu on the smallest one and kept the 640 Gb for files using Ext 3

Here is an output from : 
```
sudo fdisk -lu
```

> Disque /dev/sda: 160.0 Go, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x063c78ea

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *          63    39616289    19808113+   7  HPFS/NTFS
/dev/sda2        41945715    73400984    15727635   83  Linux
/dev/sda3        73400985    83891429     5245222+  83  Linux
/dev/sda4        83891430   312576704   114342637+   5  Extended
/dev/sda5        83891493    92277359     4192933+  82  Linux swap / Solaris
/dev/sda6        92277423   312576704   110149641    7  HPFS/NTFS

Disque /dev/sdb: 640.1 Go, 640135028736 octets
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x1ad0db90

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *          63  1250258624   625129281   83  Linux

Disque /dev/sdd: 4009 Mo, 4009230336 octets
255 heads, 63 sectors/track, 487 cylinders, total 7830528 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x000c19c9

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdd1              63     7823654     3911796    b  W95 FAT32

Disque /dev/sde: 500.1 Go, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x41ffc810

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sde1   *          63   976768064   488384001    c  W95 FAT32 (LBA)

The sda1 is Windows
The sda2 is Linux /
The sda3 is Linux /home
The sda5 is SWAP
The sda6 is Windows NTFS files

The sdb1 is Linux files in EXT3


Then
```
sudo xxd -l 2 -p /dev/sda
```
the output is
> eb48


```
sudo xxd -s 1049 -l 2 -p /dev/sda
```
the output is: 
> 01ff


```
sudo xxd -l 2 -p /dev/sdb
```
the output is:
> eb48
```
sudo xxd -s 1049 -l 2 -p /dev/sdb
```
the output is:
> 01ff


```
sudo xxd -l 2 -p /dev/sdd
```
the output is:
> fa33


```
sudo xxd -l 2 -p /dev/sde
```
the output is:
> 33c0


Then
```
sudo gedit /boot/grub/menu.lst
```
Ouput is:
> title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		07202457-5112-48ca-bc92-322e0019b3b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=07202457-5112-48ca-bc92-322e0019b3b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		07202457-5112-48ca-bc92-322e0019b3b6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=07202457-5112-48ca-bc92-322e0019b3b6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		07202457-5112-48ca-bc92-322e0019b3b6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professionnel
rootnoverify	(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1



First, the system worked and then Windows stopped to boot and only Ubuntu is still working.

Any help would be appreciated

Nicolas

---

### Post by cdtech on 2008-12-07
Your menu list should be:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professionnel
rootnoverify (**hd0,0**)
#savedefault
#makeactive
#map (hd0) (hd1)
#map (hd1) (hd0)
chainloader +1
For the first drive. It's listing the second drive in the menu list (hd1).

---

### Post by Burette on 2008-12-07
**CDTECH**

I did what you mentionned.  

I get:

> NTLDR is missing

I can also mention that yesterday I tried to boot with the windows install disk, went into **R**epair mode, did CHKDSK /R with no reported errors and then:
```
fixboot
fixmbr
```

I had the same : NTLDR is missing error so I reinstalled GRUB to at least be able to post here in UBUNTU

---

### Post by cdtech on 2008-12-07
Your ntldr is missing and must be copied from the CD. Just google NTLDR is missing.

---

### Post by Burette on 2008-12-07
I just tried this as well

> **caljohnsmith said:**
> 
Anyway, probably all you need to do to get Windows booting will be to simply replace its missing boot files. Since I also have Windows XP, to make it easy I'm attaching the three files you need to this post; just download the "WinXP_boot_files.zip" file to your Ubuntu desktop and do:
```
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```


I got not error doing this.

Still can't boot.

Still get the "NTLDR is missing"

---

### Post by Burette on 2008-12-07
Should I also point out that:

```
sudo umnount /dev/sda1
mount /dev/sda1 /mnt
cd /mnt
ls
```

Only shows me: > boot.ini  lost+found  NTDETECT.COM  ntldr

Do I understand that my WIN partition is empty or corrupted?

I am getting nervous

Last thing to mention, I have an acronis image of my Win partition but I'd like this as a last resort.

---

### Post by caljohnsmith on 2008-12-07
It looks like your sda1 partition only has Windows boot files, but not the rest of the file system. Please post the output of the following:
```
sudo umount /mnt
sudo mkdir /mnt/sda1 /mnt/sda6
sudo mount /dev/sda6 /mnt/sda6
sudo mount /dev/sda1 /mnt/sda1
cat /mnt/sda1/boot.ini
ls -l /mnt/sda6
```
Probably what happened is you installed Windows to sda6, a logical partition, so Windows put its boot files in sda1. Anyway the above commands should help clear things up. :)

---

### Post by Burette on 2008-12-07
While CalJohn was replying, I decided to recover my win partition

It works.  But now, when I:

```
sudo fdisk -lu
```
I get
> Disque /dev/sda: 640.1 Go, 640135028736 octets
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x1ad0db90

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *          63  1250258624   625129281   83  Linux

Disque /dev/sdb: 160.0 Go, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x063c78ea

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *          63    39616289    19808113+   7  HPFS/NTFS
/dev/sdb2        41945715    73400984    15727635   83  Linux
/dev/sdb3        73400985    83891429     5245222+  83  Linux
/dev/sdb4        83891430   312576704   114342637+   5  Extended
/dev/sdb5        83891493    92277359     4192933+  82  Linux swap / Solaris
/dev/sdb6        92277423   312576704   110149641    7  HPFS/NTFS

Disque /dev/sdd: 4009 Mo, 4009230336 octets
255 heads, 63 sectors/track, 487 cylinders, total 7830528 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x000c19c9

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdd1              63     7823654     3911796    b  W95 FAT32

Disque /dev/sde: 500.1 Go, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 secteurs
Units = secteurs of 1 * 512 = 512 bytes
Identifiant disque: 0x41ffc810

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sde1   *          63   976768064   488384001    c  W95 FAT32 (LBA)

My 640 GB is now the **sda** and the 160gb is the **sdb**.

I worry that something is messing with the drives priorities and it will bug sooner than later

---

