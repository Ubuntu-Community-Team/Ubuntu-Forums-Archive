---
title: "Partitioning help for netbook"
date: 2009-07-20
forum: Hardware
---

### Post by drfox on 2009-07-20
I just bought an Asus 1005-HA and need some guidance.
There are 4 partitions on the 160GB drive: 2 72GB ntfs, one small PE and something else. The first ntfs is WindowsXP, the second is "System Volume Information" and shows up as local disk D.
I figure I ought to saave the PE partition. Am I better off resizing the 2 windows partitions and installing Linux to 2 new partitions (/ and /home) or am I better off deleting the 2nd windows partition and using that space for ubuntu?

I thought I'd install UNR and then probably migrate to Xubuntu.

Thanks for any and all input and advice.

Larry

---

### Post by fxavier on 2009-07-20
I installed Ubuntu on an eee 1000he recently.  I would delete the second partition, and put extended partition there.  In the extended partition, I would put an ext3 partition, and a small swap partition.

Here's my partition layout:

sda1: Windows
sda2: extended partition
sda3: eee partition
sda4: eee partition

sda5: ext3
sda6: swap

---

