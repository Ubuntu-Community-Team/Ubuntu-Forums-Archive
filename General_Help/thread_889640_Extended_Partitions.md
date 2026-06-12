---
title: "Extended Partitions"
date: 2008-08-14
forum: General Help
---

### Post by ProgenitorVirus on 2008-08-14
Ubuntu understandably installs under an Extended Partition.

I have a Dual Boot, XP and Ubuntu on this machine.  When installing XP to repair this computer, I purposely, through the basic Windows Partitioner, left a RAW ~10GB Partition right after my Windows Partition (All in all, those 2 together were half my drive)

So I install Ubuntu, then go into Windows and format the RAW partition to FAT32.  Now, when I check my partition table, it says the FAT32 partition is under the Extended.

Will every partition I make automatically go under this?

And just on the side, if I were to manually install Ubuntu's partitions and whatnot, not using the Guided: Install using largest continuous available free space, would I still be able, through its partitioner, to get the same results as if I were to use Guided install (Have an Extended Partition with 2 Logical inside)

Thanks for all of your help!

---

### Post by coffeecat on 2008-08-14
> **ProgenitorVirus said:**
> Will every partition I make automatically go under this?

It depends. What's happened sounds like a Windows quirk to me. As you probably know, you are limited to four primary partitions, but you can have one or more extended partitions instead of primaries. And extended partitions are simply 'containers' for logical partitions. In Linux-speak, primary or extended partitions are numbered sda1, 2, 3, 4 and logicals sda5 upwards. (Or sdb1, etc for a second hard drive.) If you only had one primary and one extended you should have been able to create another primary when you created that fat32 partition, but it depends how much and what space was allocated to the extended.

> **ProgenitorVirus said:**
> And just on the side, if I were to manually install Ubuntu's partitions and whatnot, not using the Guided: Install using largest continuous available free space, would I still be able, through its partitioner, to get the same results as if I were to use Guided install (Have an Extended Partition with 2 Logical inside)

I'm not quite following you here. It sounds as though you are talking about the Ubuntu installer, but you already have an Ubuntu install - or so I understand from what you have posted.

If you do have an ubuntu install on the hard disk, try installing Gparted if you haven't already done so, and then open it by going to System > Administration > Partition Editor and see what your partitions look like in that. It gives you a nice graphical representation of the partition layout and it's easy to see how big the extended partitions are and what logicals are in them. If you need any help, post back with what you find and what you want. It would also be useful to post the output of:

```
sudo fdisk -l
```(That's a lower-case L, not one.)

---

