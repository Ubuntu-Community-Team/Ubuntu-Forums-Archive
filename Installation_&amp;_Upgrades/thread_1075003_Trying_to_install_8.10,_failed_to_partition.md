---
title: "Trying to install 8.10, failed to partition?"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by De-Apex'd 7 on 2009-02-19
I've tried several different combinations of partitions to try to get 8.10 to install and every one comes back with the same 'Failed to Partition' message.

Currently I have XP64 and Ubuntu 8.04 64-bit installed, but I'd like to replace the 8.04 with 32-bit 8.10.  However, even trying to re-partition the entire hard drive gives me the same message.

Any ideas?

Here's an fdisk -l of the current HD setup if it helps?

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f041

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5471    43945776   83  Linux
/dev/sda2   *        6080       54356   387785002+   7  HPFS/NTFS
/dev/sda3            5472        6079     4883760   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2009-02-19
When you get to the partition screen (I believe Step 4 of 7), pick Manual option and mount /dev/sda1 to / and format that partition.  You don't have to do anything with your swap partition, /dev/sda3, since the installer knows how to handle it.

---

### Post by De-Apex'd 7 on 2009-02-19
> **taurus said:**
> When you get to the partition screen (I believe Step 4 of 7), pick Manual option and mount /dev/sda1 to / and format that partition.  You don't have to do anything with your swap partition, /dev/sda3, since the installer knows how to handle it.

I think I tried that at some point and it gave me the same message, but I will try it again here and report back.

---

### Post by konqueror7 on 2009-02-19
i had a similar problem when i was installing my ubuntu also, i had problems when allocating the main ext3 partition first rather than the swap...i don't know if you got the same, just telling my experience...

---

### Post by De-Apex'd 7 on 2009-02-19
> **De-Apex'd 7 said:**
> I think I tried that at some point and it gave me the same message, but I will try it again here and report back.

Yep, I had the same message taurus.

> **konqueror7 said:**
> i had a similar problem when i was installing my ubuntu also, i had problems when allocating the main ext3 partition first rather than the swap...i don't know if you got the same, just telling my experience...

I seem to get the message referencing the swap if I tell it to format a swap and an ext3 partition.  If I only do an ext3 partition I get the message referencing the ext3 partition.  It's almost like it blows up on whichever it comes to first.

---

### Post by konqueror7 on 2009-02-19
mmm..i heard about problems when partitioning adjacent partition (the way i look it, its adjacent), what approach do you use? swap + ext3 in the first partition or ext3 first partition and swap in the last partition?

---

### Post by De-Apex'd 7 on 2009-02-20
> **konqueror7 said:**
> mmm..i heard about problems when partitioning adjacent partition (the way i look it, its adjacent), what approach do you use? swap + ext3 in the first partition or ext3 first partition and swap in the last partition?

Usually I make the first partition the ext3 and then I make the second partition the swap (saving a third partition for windows).  I've been trying to just reformat the existing partitions as well but that isn't working either.  Should I run that CD check to make sure my install CD is ok or would this problem not be caused by that?

---

### Post by konqueror7 on 2009-02-20
yes, it would be a good idea to check first (why didn't we think of that)...all this time we were blaming the partition...:o

---

### Post by CapnGimp on 2009-02-20
Is it working yet?
Try Gparted live cd for partitioning. The Ubuntu dvd gave me some problems also, but it was due to making my logical drives in vistax64 and trying to install. I had to delete the vista made partions and then I used gparted live cd even though the Ub8.10 would have worked at this point.

 I always manually partition. I ALWAYS have 1 primary and the REST extended partitions with logical drives on each of the physical disks.
 Yes windows will boot from an extended partition.

---

### Post by De-Apex'd 7 on 2009-02-21
> **CapnGimp said:**
> Is it working yet?
Try Gparted live cd for partitioning. The Ubuntu dvd gave me some problems also, but it was due to making my logical drives in vistax64 and trying to install. I had to delete the vista made partions and then I used gparted live cd even though the Ub8.10 would have worked at this point.

 I always manually partition. I ALWAYS have 1 primary and the REST extended partitions with logical drives on each of the physical disks.
 Yes windows will boot from an extended partition.

I haven't had a chance to fiddle around with it yet.  I'll probably try some things today.

So is Gparted just a partitioning tool?  Do you go in with Gparted, partition, and then proceed to the Ubuntu cd?

---

### Post by De-Apex'd 7 on 2009-02-21
Got it installed!  I guess this was a user error issue, it wasn't installing the partition as 'primary' and I wasn't forcing the issue.  Once I told it to partition ext3 as primary it worked.  Thanks for the help guys.

---

### Post by CapnGimp on 2009-02-21
User Error has been my problem 90% of the time :D

Congrats and enjoy.

---

