---
title: "Partition not showing in raid1 (fakeraid)"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by s_gnac on 2007-09-01
Hi,

I am using ubuntu 7.04 AMD64 and fakeraid (raid controller is intel ICH8R).
I have 4 SATA disk, two in a raid0 array and two in a raid1 array.

The strange thing is that Raid0 works fine but in partition in raid1 does not appear in /dev/mapper even if I can see them with fdisk. 

I can mount either drive of the raid1 Array and see the data, but if i try to write, when i reboot under Windows, the files written are either invisible, or windows say that they are corrupted and I have to do a file system check to normalize the situation

Do you know how to cure this? Any help will be appreciated.

content of /dev/mapper : I can see the partition on raid0 but not raid1
```

#ls /dev/mapper
control                 
isw_bgbfhgddjj_RAPTOR01  
isw_bgbfhgddjj_RAPTOR05  
isw_bgbfhgddjj_RAPTOR07
isw_bgbfhgddjj_RAPTOR0 
isw_bgbfhgddjj_RAPTOR02  
isw_bgbfhgddjj_RAPTOR06  
isw_cdbchafecj_SECURE1

```

Even if i see the partition with fdisk
```

#sudo fdisk /dev/mapper/isw_cdbchafecj_SECURE1
Commande (m pour l'aide): p
Disque /dev/mapper/isw_cdbchafecj_SECURE1: 320.0 Go, 320070483968 octets
255 têtes, 63 secteurs/piste, 38913 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

                      Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/mapper/isw_cdbchafecj_SECURE1p1               1       38912   312560608+   7  HPFS/NTFS

```

To compare, here is what fdisk say on the Raid0 array
```

#sudo fdisk /dev/mapper/isw_bgbfhgddjj_RAPTOR0
Commande (m pour l'aide): p
Disque /dev/mapper/isw_bgbfhgddjj_RAPTOR0: 300.0 Go, 300074401792 octets
255 têtes, 63 secteurs/piste, 36481 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

                      Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p2            3825       36481   262317352+   7  HPFS/NTFS
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p3            1913        3824    15358140    5  Extended
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p5            1913        3129     9775521   83  Linux
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p6            3130        3379     2008093+  82  Linux swap / Solaris
/dev/mapper/isw_bgbfhgddjj_RAPTOR0p7            3380        3824     3574431   83  Linux

```

And if necessary an extract of lspci :
```

#sudo lspci
00:1f.2 RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)

```

Anthony

---

