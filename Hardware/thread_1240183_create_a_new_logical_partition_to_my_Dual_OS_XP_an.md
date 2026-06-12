---
title: "create a new logical partition to my Dual OS XP and Ubuntu"
date: 2009-08-14
forum: Hardware
---

### Post by AnasZ on 2009-08-14
Hi, 
i have successfully installed Ubuntu to my laptop toshiba satallite pro along with my XP. i selected the automatically ubunto partitioning, 
however now i have 50 GB out of 230GB hard disk to windows. 
i would like to create a new partition 150GB (logical one, FAT 32) in order to put all my data which comes from ubuntu and XP as well. 
i understood that in this way i can reach these data from both systems (UBUNTU AND XP) 
can anyone give me a step by step the way to create this new partition as i am new to Ubuntu. 
thank you,

---

### Post by Bucky Ball on 2009-08-14
You should consider setting up a 'shared' partition. This would be in a format both Windows and Ubuntu recognise (FAT, NTFS).

The partitions you want to work on must be UNMOUNTED to manipulate therefore it is best to do it from the Ubuntu install CD or download a LIVE ISO of Gparted and boot from that if you are wanting to shrink OS partitions. Back up any data.

If you boot from the live CD, 'Try out Ubuntu' from the disk and once on the desktop open System->Admin->Partition Editor. Now you can shrink and create as you wish.

If you just want to create a partition from some free space, just do System->Admin->Partition Editor and go for it. Just remember, the partitions need to be UNmounted to work on. To unmount, open a terminal and type:
```

sudo umount Name-Of-MountPoint
```... where 'Name-Of-MountPoint' is the name of your mount point (!).

To mount again:

```
sudo mount -a

or 

sudo mount Name-Of-MountPoint
```



Good luck. :)

---

### Post by AnasZ on 2009-08-15
thank you Bucky for yr reply, can i do that when i am running Ubuntu:
i checked my hard it shows the following:
partition   filesystem mount point   size     used    unused   flags
/dev/sda1   ntfs                     50.31GiB   ---      ---    boot
/dev/sda2   ext3       /            242.01GiB   6.77GiB 235.24GiB
/dev/sda3   extended                  5.78GiB   ---      ---
  /dev/sda5 linux-swap                5.78GiB   ---      ---

and when i right click on the /dev/sda2 i have the option of Unmount
do you think i can unmount this and do your earlier steps?

---

### Post by Bucky Ball on 2009-08-15
> **AnasZ said:**
> thank you Bucky for yr reply, can i do that when i am running Ubuntu:
i checked my hard it shows the following:
partition   filesystem mount point   size     used    unused   flags
/dev/sda1   ntfs                     50.31GiB   ---      ---    boot
/dev/sda2   ext3       /            242.01GiB   6.77GiB 235.24GiB
/dev/sda3   extended                  5.78GiB   ---      ---
  /dev/sda5 linux-swap                5.78GiB   ---      ---

and when i right click on the /dev/sda2 i have the option of Unmount
do you think i can unmount this and do your earlier steps?

sda2 is your Ubuntu install so you would need to resize that from the live disk, not while running Ubuntu.

One thing; you have your swap in its own extended partition. It doesn't need to be. You could delete the swap, delete the 5.78Gb extended partition and then recreate a 5.78 swap (just use whatever space is left after you have deleted swap and extended partition).

---

