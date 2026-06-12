---
title: "Adding a new partition?"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by Aurels on 2005-10-27
Hi.

I added a partition to my HDD with cfdisk.
The problem that I encoure is that when I try to format it with
```
sudo mkfs.vfat /dev/hda6
```
I get a message which says that file /dev/hda6 does not exist!

When I run
```
ls /dev | grep hda
```
hda6 isn't in the list.

Have I to add it manually to /dev? If yes, how to do this?

Thanks!

---

### Post by sk545 on 2005-10-27
As far as i know 'sudo mkfs.vfat /dev/hda6' formats a partition, and doesnt make one.  Fdisk is that one that makes partitions.  To see if your current partition table, run this command:

```
$ sudo fdisk -l /dev/hda
```

Another one to try is:

```
 $ sudo cfdisk  
```

by the way, you posted this thread in the wrong forum.  This forum is only for tips/tricks.

---

### Post by Koybe on 2005-10-27
I think you're in the wrong forum.

Anyway did you write the partition table before exiting cfdisk and reboot after that?

---

### Post by bam on 2005-10-27
yup wrong forum...

---

### Post by darrenrxm on 2005-10-28
And while everyone is complaining. Why don't you use gparted to make the partition?

---

### Post by Aurels on 2005-10-28
[QUOTE=sk545]As far as i know 'sudo mkfs.vfat /dev/hda6' formats a partition, and doesnt make one. [/QUOTE]

As I said in my topic, I created the partition with cfdisk and I want to format it with mkfs.vfat

[QUOTE=Koybe]I think you're in the wrong forum.

Anyway did you write the partition table before exiting cfdisk and reboot after that?[/QUOTE]

I didn't know where to post my topic exactly? Where should it be posted?
Sorry.

Yes I tried to restart and /dev/hda6 now exists.

Thank you.

---

