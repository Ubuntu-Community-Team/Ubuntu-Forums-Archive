---
title: "Issue with more than 4 primary partitions."
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by brajan on 2006-09-04
I am relatively new to Linux. I have been using Windows and other flavors of unix for quite some time though

The issue I have is as follows:
1. I have a dell Inspiron laptop partitioned in the following manner:

(Attaching the screenshot of partitions from the 'Gparted' tool below

I have 4 partitions already ie.
1. NTFS for Windows boot
2. NTFS for Windows backup
3. FAT32 - which is for dell system restore i believe
4. FAT16 - For dell windows diagnostics

2. I need to dual-boot Windows and Ubuntu. And I am presently having Windows XP machine.

Now I need to install Ubuntu on the system. Using GParted tool, I tried to put in proper partitions.

After going through various documentation, I figured that I would be need a root(/) primary partition for Ubuntu, and another primary partition for swap.

For that I would need to merge the two NTFS partitions together and remove the FAT32 partition.
My questions are following:
1. Can I create an additional extended partition without removing the primary partitions existing now?
2. What would be the best way to go around the limitation of these 4 primary partitions?

Please let me know the best way around, till I'll play around with the live CD. :)

Cheers, Biju

---

### Post by croak77 on 2006-09-05
You can only have 4 primary partitions. The best way is a combination of primary and extended. You might be better off having 3 primary and 1 extented which contain 2 logical partitions ( swap and /root ).

---

### Post by amo-ej1 on 2006-09-05
Indeed, 4 primary partitions is the limit and there's no way around it. There are some tricks, one of those trick is to use extended partition which can contains various logical partitions, another (linux only) trick is to use LVM. Then you 'give' a partition to LVM and you can play around with the partitions all you want within LVM.

---

### Post by azraelx401 on 2006-09-05
If you send a complaint email to Dell Support complaining about the partitions that they put on there they will send you what's on them on disk.  So that way you can just get rid of at least one.  I did that and I got my disks a few days later in the mail.

---

### Post by brajan on 2006-09-05
Thanks,

So I think you are both suggesting the 4 partitions:

1. NTFS for Windows boot
2. NTFS for Windows backup
3. FAT32 - which is for dell system restore 
4. Extended partition having 3 logical partitions
   a. /root
   b. swap 
   c. The previous FAT16 

If I put the linux root on extended, would be considered as boot ? Or do i need to make any other tweaks ? Any help on this ?

Also most importantly, would the above partitioning work fine?

Cheers.Biju

---

### Post by brajan on 2006-09-05
Hi,

Just to confirm, would the above partitioning be the best possible solution?

Cheers.Biju

---

