---
title: "External USB drive - what the fsck?"
date: 2008-09-18
forum: General Help
---

### Post by brallan on 2008-09-18
a bit of advice would be greatly appreciated with this...

I'm the IT volunteer at a social center in Barcelona (canmasdeu.net). Our  video/film/documentary library is on a 500G USB external drive (FAT32) and we are unfortunately too poorly funded to buy a backup, so im hoping to recover the data on this damaged drive. 

Though recognized correctly as a disk, it makes both Explorer in XP and nautilus in Ubuntu crash (the desktop disappears) and everything grinds to a snails pace while trying to open the disk. XP cannot, but at least nautilus is able to (painfully slowly) see whats inside.

Both scandisk (the XP equivalent) and Partition Magic simply crashed when trying to recover the fs.

any help would be greatly appreciated:

sudo dosfsck -r /dev/sdc1

gives:```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:03/1d, 68:b1/3d, 69:aa/ef, 70:63/14
1) Copy original to backup
2) Copy backup to original
3) No action
? 
```

choosing either 1 or 2 gives me the error:

```
Got 7045120 bytes instead of 61032096 at 16384
```

sudo fdisk -l 
```
Disco /dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8d399bc0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       60800   488375968+   c  W95 FAT32 (LBA)

```

sudo blkid /dev/sdc1
```
/dev/sdc1: LABEL="Elements" UUID="63AA-B103" TYPE="vfat" 

```

Anybody know why dosfsck can't fix this?

---

### Post by Pro-reason on 2008-09-18
It looks like the system is too badly damaged for a fsck operation to succeed.  Instead, you ought to resort to [techniques to recover files]("https://help.ubuntu.com/community/DataRecovery") rather than fix the system.  Then, you can reformat the drive (perhaps with a superior filesystem such as ext3) and put the files back on it.

I hope your Centre didn't have anything too irreplaceable on there.

---

