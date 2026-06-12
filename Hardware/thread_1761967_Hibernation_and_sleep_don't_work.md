---
title: "Hibernation and sleep don't work"
date: 2011-05-18
forum: Hardware
---

### Post by balisto on 2011-05-18
Hi

Hibernation and sleep don't work on my PC, I use Ubuntu maverick amd64.
My motherboard is P5N-E-SLI

Can you help me please ?

Thanks

---

### Post by balisto on 2011-05-20
please

---

### Post by SecretCode on 2011-05-20
How much ram do you have? How big is your swap partition?

You could get these with the commands
```
free -m
```
```
sudo parted -l
```

---

### Post by balisto on 2011-05-21
sorry it's in french :

```
             total       used       free     shared    buffers     cached
Mem:          2007       1079        928          0         71        399
-/+ buffers/cache:        609       1398
Swap:         1952          0       1952

``````
~$ sudo parted -l
Modèle: ATA SAMSUNG HD321KJ (scsi)
Disque /dev/sda : 320GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      32,3kB  50,0GB  50,0GB  primary  ntfs                 démarrage
 2      50,0GB  73,2GB  23,2GB  primary  ext4
 3      73,2GB  75,2GB  2048MB  primary  linux-swap(v1)
 4      75,2GB  320GB   245GB   primary  ext4


Modèle: ATA WDC WD6400AAKS-0 (scsi)
Disque /dev/sdb : 640GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type     Système de fichiers  Fanions
 1      32,3kB  640GB  640GB   primary  ext3


Modèle: ATA SAMSUNG HD103SJ (scsi)
Disque /dev/sdd : 1000GB
Taille des secteurs (logique/physique) : 512o/512o
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      32,3kB  1000GB  1000GB  primary  ext4



```

---

### Post by SecretCode on 2011-05-21
Pas de probleme :)

It looks like you have exactly 2GB of swap partition. And that amount of memory. It's not clear what the exact truth is, but some sources say you need a little bit more in the swap partition than your RAM size. In any case, I'm able to hibernate with 2.1GB of swap (also with maverick amd64).

However, none of this explains the **suspend **problem as that doesn't rely on writing to disk, so I don't suggest changing your partitioning yet. You might have enough.

I think you will have to do some research - there are lots of threads about suspend and hibernate problems - [this one]("http://ubuntuforums.org/showthread.php?t=1614891") might help

---

### Post by gbrandys on 2011-08-14
I also have an ASUS P5N-E Sli and the same problems described. Don't think these features ever worked for me.

Running 2.6.32-33-generic-pae #72-Ubuntu SMP
```
free -m
             total       used       free     shared    buffers     cached
Mem:          4020       2185       1835          0        329        891
-/+ buffers/cache:        963       3057
Swap:        10236          0      10236
```

---

