---
title: "How to resize/move extended partition to the left?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by r.osmanov on 2009-09-08
Hi guys. I need extend an "extended" partition left to the first sectors.
Here is layout: 
 
```
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d9f2d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3946    31696213+  83  Linux
/dev/sda2            3947       19457   124592107+   5  Extended
/dev/sda5   *        4122        4133       96358+  83  Linux
/dev/sda6            4134        4498     2931831   83  Linux
/dev/sda7            4499        6930    19535008+  83  Linux
/dev/sda8            6931       10577    29294496   83  Linux
/dev/sda9           10578       18910    66934791   83  Linux
/dev/sda10          18911       19457     4393746   82  Linux swap / Solaris
/dev/sda11           3947        4121     1405624+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000332e4

```I don't need /dev/sda1 now. So I want extend /dev/sda2 to consume full space of /dev/sda1 as well.
GParted doesn't allow to do this, or I merely omit something . How can I do it?

Regards.

---

### Post by earthpigg on 2009-09-08
boot from an ubuntu live cd and run gparted from there, if you aren't already doing that :D

---

### Post by Bucky Ball on 2009-09-08
> **earthpigg said:**
> boot from an ubuntu live cd and run gparted from there, if you aren't already doing that :D

+1

Remember, whatever patition you are trying to manipulate needs to be UNMOUNTED. That is why you can't change the Ubuntu partition itself.

---

### Post by r.osmanov on 2009-09-08
Of course, I tried it. I boot from Live CD. And I didn't find how to resize the partition.
It merely doesn't show me corresponding options.
I can do everything with partitions within the extended partition. And there is no problem to do anything with /dev/sda1. But I don't know, how can I merge them.

---

### Post by Bucky Ball on 2009-09-08
Back one up, kill the partition, stretch the other one into the free space you have created, drop your backed-up files back in the stretched partition.

---

### Post by beameup on 2009-09-08
The swap may be mounted. You have lock symbols by the drives in GParted?
Can right click on swap and hit swapoff.

---

### Post by r.osmanov on 2009-09-08
> **Bucky Ball said:**
> Back one up, kill the partition, stretch the other one into the free space you have created, drop your backed-up files back in the stretched partition.
Okay, I kill /dev/sda1 and thus get unallocated area. Do you mean I should drag the left side of /dev/sda2 toward unallocated area? So this is my problem. I cannot do that.

---

### Post by Mka on 2009-09-08
Use GParted to delete /dev/sda1 and, with all partitions unmounted, drag the left edge of the extended partion to the left (or select it and click Resize and insert 0MB at the left) and then drag the right edge, if necessary to the right. Apply changes and reboot.

---

### Post by r.osmanov on 2009-09-08
> **beameup said:**
> The swap may be mounted. You have lock symbols by the drives in GParted?
Can right click on swap and hit swapoff.
Hmm, I didn't care about it. I'll try to swap them off. 
I'll return here to tell if it helped. Indeed, why did I forgot about swaps...:confused:

Thanks. And thanks to all of you, guys.

---

### Post by Bucky Ball on 2009-09-08
> **r.osmanov said:**
> Okay, I kill /dev/sda1 and thus get unallocated area. Do you mean I should drag the left side of /dev/sda2 toward unallocated area? So this is my problem. I cannot do that.

You need to do it from System->Admin->Partition editor booting from a LIVE CD. The partitions need to be UNMOUNTED and if you are running Ubuntu from the hard drive it can't be unmounted.

Looks like your os is in the extended partition which is sda2. You need to unmount that and all the logical partitions in it. If you boot from CD they won't be mounted in the first place.

---

### Post by r.osmanov on 2009-09-08
Yeah, it worked perfectly! :D
It is so simple! All I needed is to swap off a couple of partitions.
Then I moved partitions to the left one-by-one freely. Everything took about 5 minutes.

Thanks a lot.

---

### Post by Bucky Ball on 2009-09-08
Good work. You can unmount any partition when you are booted from the hard drive install by right clicking EXCEPT the one Ubuntu OS is on.

---

### Post by beameup on 2009-09-08
{BeaMeUp in his best Hannibal Smith voice says} "I love it when a plan comes together" :)

---

