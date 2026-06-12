---
title: "Disk Partitioning"
date: 2010-06-21
forum: Hardware
---

### Post by ironvital on 2010-06-21
Hi everyone:)

I am new to Linux and I wonder if anyone can help me with disk management.

my partitions are:
/dev/sda1  -  Recovery (Primary)
/dev/sda2  -  System Reserved (Primary) this one is bootable
/dev/sda3  -  C: (Primary) this one has Windows 7 on it
/dev/sda4  - this one is Extended and has two logical drives, one for Ubuntu, second for Swap

So, what I want to do is shrink the C: drive with Windows 7. Then take the unallocated space and turn it into a logical drive of the Extended partition.
Is it possible?
Thank you for your attention:)

---

### Post by wilee-nilee on 2010-06-21
> **ironvital said:**
> Hi everyone:)

I am new to Linux and I wonder if anyone can help me with disk management.

my partitions are:
/dev/sda1  -  Recovery (Primary)
/dev/sda2  -  System Reserved (Primary) this one is bootable
/dev/sda3  -  C: (Primary) this one has Windows 7 on it
/dev/sda4  - this one is Extended and has two logical drives, one for Ubuntu, second for Swap

So, what I want to do is shrink the C: drive with Windows 7. Then take the unallocated space and turn it into a logical drive of the Extended partition.
Is it possible?
Thank you for your attention:)

Shrink the W7 as you suggest with the disk manger in windows. Then look at gparted with a live cd and you can expand the logical then the primary inside if there is space, I believe you have to turn off the swap with a right click on it to do so.

You might post a screen shot of the HD from gparted to help with helping

---

### Post by oldfred on 2010-06-21
If they are adjacent it should be relatively easy. Use the windows tools to shrink c: sda3. Then use gparted to move the extended partition to include the unallocated and you can create a new partition. If they are not adjacent then it is more complicated.

---

### Post by ironvital on 2010-06-30
Thanks guys, you are awesome:)

I have shrunk the C: drive in Windows, then I used GParted to expand the Extended volume to include the unallocated space:)
Now I don't have to worry about losing the data:)

Thank you!!!!!!!

---

