---
title: "Can't remove boot flag--and no &quot;a&quot; option showing in fdisk."
date: 2017-07-07
forum: Hardware
---

### Post by whereismymindat2 on 2017-07-07
For some reason, my USB drive acquired a boot flag and won't mount. I'm trying to remove the boot flag, however I don't have the "a" option (per norm) in my fdisk options. What other method can I try? 

Also, thi sis the very first time (I've run fdisk 100's of times) never seen results like this. it's showing "/dev/ram0" and so on. Why is this occurring? 

My fdisk -l options. 


```


banter@Dawg:~$ sudo fdisk -l
[sudo] password for banter: 
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


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 05A05D70-2730-0A46-B531-7D9ADCDB522B

Device          Start        End   Sectors   Size Type
/dev/sda1        2048   19531344  19529297   9.3G Linux filesystem
/dev/sda2    19531776   39063551  19531776   9.3G Linux filesystem
/dev/sda3    39063552   97656831  58593280    28G Linux filesystem
/dev/sda4   210937856  230469105  19531250   9.3G Linux filesystem
/dev/sda5  1910157312 1929689087  19531776   9.3G Linux swap
/dev/sda6   367187968  855470079 488282112 232.9G Linux filesystem
/dev/sda7   855470080  933595135  78125056  37.3G Linux filesystem
/dev/sda8   933595136 1519532031 585936896 279.4G Linux filesystem
/dev/sda9  1519532032 1910157311 390625280 186.3G Linux filesystem
/dev/sda10  269531136  367187967  97656832  46.6G Linux filesystem
/dev/sda11   97656832  195313663  97656832  46.6G Linux filesystem
/dev/sda12  230469632  269531135  39061504  18.6G Linux filesystem

Partition table entries are not in disk order.




Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F171C8C8-6FD2-4BBF-B12F-21547A5C6067
banter@Dawg:~$ 

 

```

The * on /dev/sdb means it's a boot flag, correct? 

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes


THIS is what fdisk shows 

```


root@Dawg:~# fdisk /dev/sdb

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): a
a: unknown command

Command (m for help): m

Help:

  Generic
   d   delete a partition
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition
   p   print the partition table
   t   change a partition type
   v   verify the partition table
   i   print information about a partition

  Misc
   m   print this menu
   x   extra functionality (experts only)

  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file

  Save & Exit
   w   write table to disk and exit
   q   quit without saving changes

  Create a new label
   g   create a new empty GPT partition table
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table


Command (m for help): 

```

Thank you in advance for help.

---

### Post by oldfred on 2017-07-07
Boot flag is not the issue.
Grub does not use boot flag. Windows with BIOS requires boot flag on primary NTFS partition with its boot files.
UEFI/gpt systems require a boot flag if using gparted on the FAT32 partition that is the ESP - efi system partition. But flag is not same as BIOS/MBR as with gpt parted/gparted just use boot flag to assign a very long GUID that then UEFI knows is the bootable partition.

But we have seen UEFI/BIOS that will not even let you start to boot unless it sees a partition with a boot flag, so we still suggest every drive have one (and only one) partition with a boot flag.

I normally use gpt and include an ESP on every drive including all flash drives. Only Ubuntu installer is often MBR, but it must have boot flag.

You are not showing any partitions on sdb? Do not format the drive, but create partition(s) and format those.

Some Ubuntu flavors seem to use the ram disks, I do not think Ubuntu itself does, as I do not normally see those. But many have posted with those.

---

