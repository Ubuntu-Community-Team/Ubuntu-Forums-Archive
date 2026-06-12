---
title: "New to linux, partition problems"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Abzddon on 2009-06-29
I recently installed Ubuntu 9.04 along side windows. During installation it said its making a partition for linux, and being new at this i had no idea that i had to increase the size of the partition manually, nor was I warned or told during the  process of intallation.

So now i have linux installed but it has no space to install anything at all. Ive been through many forums, but none of them are helpful to me.

Basically ive got 2 HDD in my computer. I think the linux drive is installed on the second one, but not sure. I tried out a few things by reading many forums, and that has not helped one bit. Now I have loads of partitions, which i made SDA3, but linux still doesn't use it. I also had a scenrio where i made an unused partition, but i cannout expand/ merge the linux partition to use it, although they are right next to each other.

I don't know what to do, and i think ive just made everything much worse.

I read in some forum to type sudo fdisk-l (to help you understand the probelm better).
heres the result:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda08a27d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13687   109940796    7  HPFS/NTFS
/dev/sda2           14593       14593        8032+  82  Linux swap / Solaris
/dev/sda3           13688       14592     7269412+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9455

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13621   109410651    7  HPFS/NTFS
/dev/sdb2           19132       19457     2618595    5  Extended
/dev/sdb3           13622       19131    44259075    b  W95 FAT32
/dev/sdb5           19132       19435     2441848+  83  Linux
/dev/sdb6           19436       19457      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0002494b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1000      255983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(998, 15, 32) logical=(999, 15, 31)

**And then df - h**

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             2.3G  2.3G     0 100% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  172K  501M   1% /dev
tmpfs                 501M  484K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp


Hope this is enough info.

Also I noticed when trying to increase the size of the linux partition (sdb3) to the unused partition, i was unable to do it. I think its because they where in 2 different catagories. In gparted it showed 2 different arrows in the textbox, the first one was the windows partition and the second was linux. After i shrank the windows partition, a new arrow appeared with unused partition, which the linux partition didnt merge into.

However when i shrank the linux partition, a new arrow also appeared with unused partition, but it was in the sub-catagory of the overall linux partitions :-s .

All of this was on the second HDD, where the linux partition is, i think. Its the only place with a sdb3, and the primary HDD had nothing but an unused partition, which i made into a sda3:p.... it didnt work though ](*,) .

What should i do??

Thanks for the help.

---

### Post by merlinus on 2009-06-29
FWIW, sdb3 is a fat partition.  linux is on sdb5.

Given what is done, your easiest route is to reinstall.  Back up important data first.

Also, you may wish to use your entire second hdd for linux, and leave windows on the first. 
If you choose to do this, then post back if you need assistance with partioning schemes.

---

### Post by TheGreenFox on 2009-06-29
From what I understand, you have two hard drives, one with Windows and you are trying to install Ubuntu on the other.

The simplest solution would be to physically unplug the Windows hard drive. After you start the install on step 5 you should get an option to ether resize any current partitions, have a particular hard drive be automatically partitioned for you, or to do it manually. Simply pick to have it partitioned for you. 

Good Luck,

TheGreenFox

---

### Post by Abzddon on 2009-06-29
Alrighty thanks for the replies.

Ive got it done, its all working fine now =D> .

Basically went back onto my beloved windows xD.... and deleted every partition on the 2nd HDD, including the linux ones. Then installed linux on the whole of the 2nd HDD as mentioned, and its working gr8 now! ;)

Also made a partition on the HDD and made the partition a FAT32 so my windows has more space, and this i believe also allows linux to use it. I hope i havent done anything wrong there [-o< .

Thanks for all your help, now lets hope all this trouble for Linux was worth it lol.

Peace

---

