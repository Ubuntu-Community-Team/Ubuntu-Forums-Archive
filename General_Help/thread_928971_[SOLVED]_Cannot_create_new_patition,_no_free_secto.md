---
title: "[SOLVED] Cannot create new patition, no free sector available"
date: 2008-09-24
forum: General Help
---

### Post by Sun@~ on 2008-09-24
I just reinstalled a server with Ubuntu 8.04LTS server edition. I created 4 paritions: /boot, /, swap, /home while booting with CD. After finish installation, I want to create new partition. I run the command #fdisk /dev/sda then press n but it show up [COLOR="Red"]no free sector available[/COLOR] message and cannot proceed. I still have about 80G free disk space:(. Can somebody tell me what is the problem and how to solve it? This is quite urgent, thank you.

---

### Post by snowpine on 2008-09-24
You can only have 4 primary partitions. What you need to do is create 3 primary partitions, then one extended partition. You can create as many logical partititions as you like within the extended partition, bringing your total to 5 (or more).

Obviously you should do this while booting from a live CD.

Hope that helps you out!

---

### Post by Sun@~ on 2008-09-24
> **snowpine said:**
> You can only have 4 primary partitions. What you need to do is create 3 primary partitions, then one extended partition. You can create as many logical partititions as you like within the extended partition, bringing your total to 5 (or more).

Obviously you should do this while booting from a live CD.

Hope that helps you out!

Thanks for your quick reply. During installation I only created 2primary partitions, and 1 logical partition. The extended was automatically exist and sum up the logical partitions' disk space. I plan to create new partition afterward. Normally #fdisk /dev/sda, press n to create new patition then can choose whether want primary or extended partiton. Not that I should be able to do this without booting from CD:confused:? What mean by the message [COLOR="Red"]"no free sector available"[/COLOR] that stop me from doing this? I am doing remote access through SSH so I cannot boot from CD.

---

### Post by plucky on 2008-09-25
> What mean by the message "no free sector available" that stop me from doing this?

Fdisk thinks your disk drive has no un-allocated space available.i.e the partition table is full.

> I created 4 paritions: /boot, /, swap, /home while booting with CD

or

> During installation I only created 2primary partitions, and 1 logical partition.

Which is correct?

Please post output of ```
sudo fdisk -l
```

---

### Post by Sun@~ on 2008-09-25
Output of ```
sudo fdisk -l
```

Disk /dev/sda: 146.8 GB, 146815733760 bytes
255 heads, 63 sectors/track, 17849 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8769ddd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        4875    39062047+  83  Linux
/dev/sda3            4876        7307    19535040    5  Extended
/dev/sda4            7308        7793     3903795   82  Linux swap / Solaris
/dev/sda5            4876        7307    19535008+  83  Linux

---

### Post by plucky on 2008-09-25
> **Sun@~ said:**
> Output of ```
sudo fdisk -l
```

Disk /dev/sda: 146.8 GB, 146815733760 bytes
255 heads, 63 sectors/track, 17849 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8769ddd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13        4875    39062047+  83  Linux
/dev/sda3            4876        7307    19535040    5  Extended
/dev/sda4            7308        7793     3903795   82  Linux swap / Solaris
/dev/sda5            4876        7307    19535008+  83  Linux

According to that printout,you have 4 primary partitions,which is why you cannot add the un-allocated space.

sda1,sda2 and sda4 are primary partitions and sda3 is the extended partition and also a primary and contains sda5,a logical partition.

You could delete the swap partition and put it into the extended partition,but I am not sure how to do that using fdisk as I see no way of resizing partitions in fdisk. Remember you have to un-mount partitions to change them.

This can easily be done using a Live CD.


Good Luck

---

### Post by Sun@~ on 2008-09-25
> **plucky said:**
> According to that printout,you have 4 primary partitions,which is why you cannot add the un-allocated space.

sda1,sda2 and sda4 are primary partitions and sda3 is the extended partition and also a primary and contains sda5,a logical partition.

You could delete the swap partition and put it into the extended partition,but I am not sure how to do that using fdisk as I see no way of resizing partitions in fdisk. Remember you have to un-mount partitions to change them.

This can easily be done using a Live CD.


Good Luck

oh..!!! I forgot that the automatic created extended partition is consider as a primary partition. No need resizing, just delete and add back the sawp as logical I think can already.

Thank you very much.:)

---

### Post by plucky on 2008-09-25
Can you mark this thread as **solved** using [color=red]Thread Tools[/color] at top of page.

Thanks

---

