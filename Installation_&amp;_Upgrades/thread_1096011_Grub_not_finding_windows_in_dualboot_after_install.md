---
title: "Grub not finding windows in dualboot after install 8.10"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by djmaxmalta on 2009-03-14
hey,

here is my current scenario,

my pc specs,

Intel celeron D 3.06gh
2gig 667 ram
nvidia Geforce 8400gs

1x ide 160gb (codename: external back up since i have the case for it but i done it directly into the tower to copy some stuff)

1x Sata 160gb (codename ubuntu & windows xp)

1x sata 500gb (codename: Backup500

1x DVD writer combo with securerom sata

1x dvd reader/cd writer ide

my problem is that my 500 in windows is c:
and windows xp is h:
and i forgot the what the other 160 was, and i had deamon tools on xp

what i am surprised is how in the hell grub didn't find my xp automatic i had to downgrade from windows 7 to xp to have ubuntu dual booting with xp and no i didn't want to do a wubi install but i think that would of been less hassle...

how can i edit/tell grub that there is xp on the same hdd as ubuntu? as ubuntu finds all 3 hdds and flopy drive and disc drives

---

### Post by zvacet on 2009-03-14
```
sudo fdisk -l
```

Post it here.

---

### Post by djmaxmalta on 2009-03-14
> **zvacet said:**
> ```
sudo fdisk -l
```

Post it here.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x546d7da8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e2d3e2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          65      522081   82  Linux swap / Solaris
/dev/sdb2            5100       19456   115322602+   f  W95 Ext'd (LBA)
/dev/sdb3              66        5099    40435605   83  Linux
/dev/sdb5            5100       19456   115322571    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11d68a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488383488    7  HPFS/NTFS



here is what it posted and i used grub editor for kde to get windows but still it made more of a mess how could i fix this without re-formating?

---

### Post by meierfra. on 2009-03-14
Did you deleted any partitions after installing XP?  It seems that the partition containing the boot files got deleted.  

To confirm:

```
sudo mount /dev/sdc1 /mnt
ls -l /mnt
```

If this does not show the files "boot.ini", "NTLDR" and "NTDETECT.COM",  the boot files are indeed missing.  

To recover your boot files and configure menu.lst, use this tutorial:

[http://ubuntuforums.org/showthread.php?t=813628]("http://ubuntuforums.org/showthread.php?t=813628")

---

### Post by djmaxmalta on 2009-03-15
hey man i just got bored with out a system and re-formated the whole thing to xp then will do wubi

---

### Post by meierfra. on 2009-03-15
```
re-formated the whole thing to xp
```
As long as you won't have to spend to much time configuring XP, that might be the fasted solution.

> then will do wubi 
In my opinion, wubi saves you some time  at the beginning, but gives you more problems in the long run.

---

### Post by djmaxmalta on 2009-03-16
> **meierfra. said:**
> ```
re-formated the whole thing to xp
```
As long as you won't have to spend to much time configuring XP, that might be the fasted solution.


In my opinion, wubi saves you some time  at the beginning, but gives you more problems in the long run.


well as a wubi maybe a small partion, but files will be saved on my other ntfs hdd's so in a way apt on cd and then upgrade to the next distro? i think it may be simpler like that? and i would be 100% ubuntu if my games could run properly

---

### Post by meierfra. on 2009-03-16
> well as a wubi maybe a small partion, but files will be saved on my other ntfs hdd's so in a way apt on cd and then upgrade to the next distro? i think it may be simpler like that? a

Could you rephrase this? I'm not sure, what you are trying to say.

If Ubuntu will be on a separated hdd, I definitely recommend using  a regular Ubuntu install and not Wubi.  I suggest using a separate Home or Data partition. It makes reinstalling a lot easier if your ever need (or want) to.

---

### Post by djmaxmalta on 2009-03-16
> **meierfra. said:**
> Could you rephrase this? I'm not sure, what you are trying to say.

If Ubuntu will be on a separated hdd, I definitely recommend using  a regular Ubuntu install and not Wubi.  I suggest using a separate Home or Data partition. It makes reinstalling a lot easier if your ever need (or want) to.

what i ment as a wubi install... git it maybe 20 gb.. and then transfer mp3 and so on from a other hardisk that is a ntfs format
or hpfs+

---

