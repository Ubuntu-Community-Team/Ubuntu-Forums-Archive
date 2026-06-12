---
title: "Fresh Install - Mount extra drives"
date: 2008-09-24
forum: General Help
---

### Post by zoomy942 on 2008-09-24
So, I reinstalled Ubuntu this morning and my extra 2 drives show up, but I don't know how to mount them.  I have been googling around, but nothing seems to be showing me a simple command to mount these drives.

```
 zimmerman@Ubuntu-desktop:~$ sudo -s
root@Ubuntu-desktop:~# fidsk -l
bash: fidsk: command not found
root@Ubuntu-desktop:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9365    75224331   83  Linux
/dev/sda2            9366        9729     2923830   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb66bb107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   83  Linux

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19930   160083968    7  HPFS/NTFS
root@Ubuntu-desktop:~# 


```

---

### Post by qstraza on 2008-09-24
```
sudo mkdir /mnt/sdc1
sudo mkdir /mnt/sdb1
sudo mount /dev/sdc1 /mnt/sdc1
sudo mount /dev/sdb1 /mnt/sdb1

```

---

