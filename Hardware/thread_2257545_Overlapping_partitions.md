---
title: "Overlapping partitions"
date: 2014-12-20
forum: Hardware
---

### Post by mfvpcrec on 2014-12-20
Hello everyone: I have a problem with my hard disk . After pull out my hard disk
of my notebook and disconnected the BIOS battery  (and clean my notebook :))
when I turned on the computer , Windows seemed to have had a problem and it couldn't be started. So Windows gave me three options, one was worse than another option but sounds good something like repair automatically. I chose that option and Windows started  OK.

When I rebooted my notebook to use Ubuntu a message appeared . Something like "The /home partition cannot be found. Press S to ignore or M to mount manually or continue to wait"

After press S I realized that /home doesn't exists and gparted says something like "can't have overlapping partitions" and all the disk bar is of grey color.

Honestly i have a poor idea of how fix this kind of problems. I read that fixpart will be fine for this kinds of problems but i dont know how use it well.

Someone know how to fix this problem without loose information?

I attached the output of fdisk -lu /dev/sda (i have one disk)
```

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   391034599   195312500    7  HPFS/NTFS/exFAT
/dev/sda3   *   391034880  1430097919   519531520    5  Extendida
/dev/sda4      1430097920  1464936447    17419264    7  HPFS/NTFS/exFAT
/dev/sda5      1464936448  1465143295      103424    c  W95 FAT32 (LBA)
/dev/sda6      1058117632  1415219199   178550784   83  Linux
/dev/sda7      1415221248  1430097919     7438336   82  Linux swap / Solaris
```

And I attached a output of fixpart

```
* NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

                                                Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       409599   primary              Y      0x07
   2                409600    391034599   primary              Y      0x07
   4            1430097920   1464936447   primary              Y      0x07
   5            1464936448   1465143295   omitted                     0x0C
   6            1058117632   1415219199   logical     Y               0x83
   7            1415221248   1430097919   logical     Y               0x82

```

Thank you for all!

---

### Post by oldfred on 2014-12-20
If a partition is labeled sda5 it must be logical and inside the extended partition, but yours was outside the extended partition.
And you can only have one boot flag per hard drive or only on sda1.

---

### Post by mfvpcrec on 2014-12-20
Thank you Olfred but how can fix it ? 
In fixpart i get

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

But i don't know how change it. Or worse if I change it i don't know if Windows will stop working. And this will be a worse situation.

---

### Post by oldfred on 2014-12-20
Not sure what that message is, but would not worry about it.

Some older tools have very old error messages.
Generally you do not want to move the start of partitions. And with Windows it can create major issues. Any resize of NTFS partitions requires a chkdsk from a Windows repairCD.

And your sda1 starts at sector 2048 which is the current standard.

---

### Post by mfvpcrec on 2014-12-20
I was trying testdisk. 

     Partition                  Start        End    Size in sectors

 ```
1 * HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
 2 P HPFS - NTFS             25 126 38 24340 198 26  390625000
 3 E extended             24340 202 55 89019 121 62 1039063040
 4 P HPFS - NTFS          89019 121 63 91188  19 31   34838528 [RECOVERY]
 5 L FAT32 LBA            91188  19 32 91200 242 50     206848 [HP_TOOLS]
Space conflict between the following two partitions
 3 E extended             24340 202 55 89019 121 62 1039063040
 5 L FAT32 LBA            91188  19 32 91200 242 50     206848 [HP_TOOLS]
   X extended             65864 165 30 88093  81 52  357103616
 6 L Linux                65864 197 62 88093  81 52  357101568
   X extended             88093  81 53 89019 121 62   14878720
 7 L Linux Swap           88093 114 22 89019 121 62   14876672
```

That means anything?

---

### Post by oldfred on 2014-12-20
Every time you edit partitions, you have another set of partitions that existed. Testdisk finds all of them, so you have to have some idea of what partitions you have and select the versions that do not overlap as that would be from different changes.

I thought fixparts showed your correct partitions and you just needed to write that. 
If you attempt to restore a mis-matched set from testdisk you may make things a lot worse.  It shows 4 different versions of your extended partition, so you have made at least 4 different sets of partitions.

---

### Post by mfvpcrec on 2014-12-20
Ok... I don't know but i have a backup of the information (more or less actualized) and i have this information about the partitions

```

/dev/sdb1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   391034599   195312500    7  HPFS/NTFS/exFAT
/dev/sdb3      1430097920  1464936447    17419264    7  HPFS/NTFS/exFAT
/dev/sdb4   *   391034880  1430097919   519531520    5  Extendida
/dev/sdb5       391036928  1058115583   333539328   83  Linux

```

I have only to return to its original shape partitions or is even worse?

---

### Post by oldfred on 2014-12-20
Boot flag must be on sdb1. 
Windows uses boot flag and has to have it on its boot partition. 
Grub does not use boot flag so if grub is working it should still boot Windows if Windows is working.

---

