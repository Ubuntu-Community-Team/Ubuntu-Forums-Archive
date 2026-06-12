---
title: "resizing ext4 partitions"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by faust99 on 2009-11-10
Hopefully someone will advise with this please...

I have a four partition scheme on my hard drive.

The order is:

Mac OS Extended 
Ext4 /
Swap
Ext4 /home

What I would like to do is shrink the Mac OS partition and somehow enlarge the ext4 /home partition. Is this possible? ):P

---

### Post by mikewhatever on 2009-11-11
You might want to post the output of **sudo fdisk -l** command to verify the order of your partitions. The way you described it, there are two other partitions between OSX and home, and if that's the case, they would need to be moved out of the way.

---

### Post by faust99 on 2009-11-11
Hi thanks for the reply. The output is:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        9530    76340636   af  HFS / HFS+
/dev/sda3            9530       10775    10000000+  83  Linux
/dev/sda4           10775       11024     2000000+  82  Linux swap / Solaris

---

### Post by mikewhatever on 2009-11-11
Is that all of the output? As you can see, sda3 is the only linux partition and sda4 is the swap. There is no partition after sda4, is there.

---

### Post by faust99 on 2009-11-11
There's something not right with the output of fdisk. I suppose it must be to do with "WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted." I didn't notice that at first ](*,)

Gparted reveals:

/dev/sda2 hfs+
/dev/sda3 ext4 /
/dev/sda4 linux swap
/dev/sda5 ext4

---

