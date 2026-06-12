---
title: "Adding space to Linux hard drive partition"
date: 2009-07-19
forum: Hardware
---

### Post by Iksf on 2009-07-19
Im a relitavly new Ubuntu user, i gave Linux 25GB to mess around on. Now iv decided to make it my main OS and i want to give it another 100GB, i have shrunk my Windows 7 partition to produce the required space however i cant work out how to add the unallocated space to my Linux partition, any ideas?

Thanks in advance

---

### Post by Elfy on 2009-07-19
Can you open a terminal and run ```
sudo fdisk -l
``` paste the output here so we can see what we are working with please.

You will need your password and -l is a lower case L

---

### Post by Malta paul on 2009-07-19
The space you allocated to the Ubuntu operating system is plenty, What I would do is make yourself another partition using your spare space. This way you will not loose any of your system data.
You can use 'Gparted' for this, from Applications>Add/remove search gparted and apply. It can then be accessed form System>Administration>Partition Editor.
To mount the partition goto Places>Removable media an click on you partition. I you wish to mount your partition at boot-up let me know and I will explain.

Backup you data first!
:)

---

### Post by Loevborg on 2009-07-19
I'll have to agree with Malta Paul's comment above. The easiest is probably just to add another partition, using the method he describes. On that partition, you can store your video files/whatever big files you have. The core system probably won't be larger than 25GB.

It is possible to enlarge the Linux partition. For that to be possible, however, that partition must be continuous with the freed up space. To try this, boot from an Ubuntu live CD and resize the partition using gparted. (This is necesarry because you cannot resize your root partition while it is mounted.) Be aware, though, that these operations are never 100% foolproof. So either make diligent backups, or use Paul's suggestion.

---

### Post by Iksf on 2009-07-19
Hmm, ok fair enough. Is there any differance between making a new one and just adding it back to Vista and making a Ubuntu only folder/

---

### Post by Iksf on 2009-07-19
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85295522

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         916     7352320   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         916       17770   135384181    7  HPFS/NTFS
/dev/sda3           17771       20768    24081435   83  Linux
/dev/sda4           20769       24321    28539472+   f  W95 Ext'd (LBA)
/dev/sda5           20769       24169    27318501   83  Linux
/dev/sda6           24170       24321     1220908+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x469d60df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)

is what i get from fdisk Forestpixie

---

