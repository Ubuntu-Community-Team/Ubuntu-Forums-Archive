---
title: "cannot mnt secondary HD"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by rudedcam on 2006-12-10
my secondary harddrive used to be mounted at all time... used to work

when i try to mount it it gives me this message.
> 
error: the peripheral /dev/hdb5 is not removable
error: impossible to execute pmount


```

rudecam@Ganesh:~$ sudo fdisk -l
Password:

Disque /dev/hda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1        1044     8385898+  83  Linux
/dev/hda2            1045        1305     2096482+  82  Linux swap / Solaris
/dev/hda3            1306        9729    67665780   83  Linux

Disque /dev/hdb: 120.0 Go, 120060444672 octets
240 têtes, 63 secteurs/piste, 15508 cylindres
Unités = cylindres de 15120 * 512 = 7741440 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1               2       15508   117232920    f  W95 Etendu (LBA)
/dev/hdb5               2       15508   117232888+   b  W95 FAT32
rudecam@Ganesh:~$ sudo mkdir /mnt/windows
mkdir: Ne peut créer le répertoire `/mnt/windows': Le fichier existe.
rudecam@Ganesh:~$ sudo mnt vfat /dev/hdb5 /mnt/windows
sudo: mnt: command not found
rudecam@Ganesh:~$

```



anyone can help me out?

thanks guys
rudecam

---

### Post by taurus on 2006-12-10
Can you paste your /etc/fstab here?

```
cat /etc/fstab
```

---

