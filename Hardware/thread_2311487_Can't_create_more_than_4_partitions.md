---
title: "Can't create more than 4 partitions"
date: 2016-01-27
forum: Hardware
---

### Post by masowymordulec on 2016-01-27
Hello,

I installed Ubuntu 15 along side with Win 10. Before installation I already had 3 partitions MBR, C:, D:. I created one more during Ubuntu installation for Ubuntu, but when I wanted to create another one for swap I couldn't. An info popped up saying that I can't create more than 4 partitions or something like that. 
I'm computer noob. I'm trying to get into computers and I never heard of partition limit before I installed Win10. I never had problems with it when installed Ubuntu along side with Win7...

Thanks for help

P.S. I haven't got SWAP at the moment because of being unable to create another partition. 

**This is fdisk -l: (what are these all ram "disks"?**)

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x17cd6448

Urz&#261;dzenie Rozruch      Start     Koniec    Sektory   Size Id Typ
/dev/sda1  *             2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2              206848  205006847  204800000  97.7G  7 HPFS/NTFS/exFAT
/dev/sda3          1362743296 1465147391  102404096  48.9G 83 Linux
/dev/sda4           205006848 1362743295 1157736448 552.1G  7 HPFS/NTFS/exFAT

Partition table entries are not in disk order.

---

### Post by Dennis N on 2016-01-27
Partition #4, The Ubuntu partition,  should have been created as extended type. Then that partition can be divided into 2 logical partitions - one for Ubuntu and one for the Swap.

(MBR partitioning allows only 4 primary type partitons - one of those can be extended instead of primary. Extended partitions can be subdivided into many logical partitions).

---

### Post by Bashing-om on 2016-01-27
masowymordulec; Hello;

Welcome to our world.
> 
I'm computer noob. I'm trying to get into computers and I never heard of partition limit

Permit me to allow TJ- to push you along the path of learning. In this case partitioning:
see:
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)
that explains the why of partitioning ..both MBR and EFI .

[INDENT][INDENT]open source
[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by weatherman2 on 2016-01-27
Dennis is correct.

Think of an Extended Partition as a "container" for other partitions called "logical" partitions.  The "extended" partition is a kludge to work around an ancient limitation of MSDOS partitions (which until the newer GPT standard were used for 20+ years) to work around the old "four is the limit" for MSDOS partitioning.  You can create as many logical partitions as you wish (within reason) inside an Extended partition.  Had you let the installer choose, it would have created an extended partition automatically.

At this point, you could either start over and wipe the 4th partition with Ubuntu and re-do it with extended + logical partitions...or you could copy off your new installation temporarily (if you've already done a lot of work on it, say) to some other disk, re-do the partitioning, and then copy the partition back to a new logical partition.  Probably easier to start over, though.

---

### Post by yoshii on 2016-01-27
GPT can do more than 4 primary partitions, MBR can only do 4 primary partitions.  This is normal behavior for any partition formatting.  
These types of things usually need to be planned ahead for.

---

### Post by tokyobadger on 2016-01-28
[quote="[**[COLOR=#000000]masowymordulec[/COLOR]**]("http://ubuntuforums.org/member.php?u=2018477")"]**This is fdisk -l: (what are these all ram "disks"?**)[/quote]
[See this askubuntu post for an explanation.](https://askubuntu.com/questions/703576/fdisk-l-shows-16-ram-disks-dev-ram0-ram15/703584) Your output is normal.
Example of an MSDOS limited disk with extended partition to work around the 4 partition limitation
```

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdd1  *         2048 195310641 195308594  93.1G 83 Linux
/dev/sdd2       195313662 500117503 304803842 145.4G  5 Extended
/dev/sdd5       195313664 207030271  11716608   5.6G 82 Linux swap / Solaris
/dev/sdd6       207032320 353515519 146483200  69.9G 83 Linux
/dev/sdd7       353517568 500117503 146599936  69.9G 83 Linux
```
BTW - how much RAM do you have?

---

### Post by Yellow Pasque on 2016-01-28
Creating a swap file would be a better/easier solution here rather than reinstalling and redoing partitions (assuming OP doesn't plan to create more partitions).

See the "Four-step Process to Add Swap File" section in: [https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)
You'll probably also want to change swappiness to 10 if using a swapfile: [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

