---
title: "Installing 32 Ubuntu and thinking of blue deers"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Deicider on 2009-07-12
I have the 64 bit version of ubuntu and it made my days difficult :S
Ok, heres the deal , i want install the 32 bit ubuntu. I have 4 partitions the 3 of them r for windoz usage and the forth (40GB) are for linux.I was thinking into making one of the winbos partitions into ext3 and then install the 32 there and from the 32 partion of ubuntu  format the 64's partition and make it a windows (ntfs)...better ways,anyone??

---

### Post by coffeecat on 2009-07-12
Before you do anything, consider this.

Because of a limitation in the MSDOS partition table design, you are limited to only four primary partitions. It sounds as though you may very well already have four primary partitions, but you will need more. To get around this limitation, you can have one (and one only per hard drive) extended partition instead of a primary. An extended partition is merely a container for a number of logical partitions. I can't remember the limit offhand, but more than you're likely to need. The advantage of Linux is that it can reside in and boot up from logical partitions, unlike Windows which needs to be in a primary - or at least the NTLDR needs to be in a primary.

At the moment, you have 3 partitions for Windows and 1 for Linux. What about a swap partition for Linux? As a minimum you need 2 partitions for Linux: one root partition and one swap. And some people like to create a separate /home partition, which would make three. So, instead of reformatting one of your Windows partitions with a Linux filesystem, you may wish to completely rethink your partition layout.

Before you go any further, boot into Ubuntu, open a terminal and post the output of:

```
sudo fdisk -l
```This will give us what we need to know about your present partition set up. Please post the output in [noparse]```

```[/noparse] tags, otherwise the fdisk output will be very difficult to read.

---

