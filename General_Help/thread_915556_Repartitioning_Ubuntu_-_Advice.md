---
title: "Repartitioning Ubuntu - Advice?"
date: 2008-09-10
forum: General Help
---

### Post by sternkanz on 2008-09-10
Hi, my current setup as gparted reports it is this:

/dev/sda1 - fat32 - 7.32GB - Windows 98 SE Partition
/dev/sda2 - extended - 141.72GB
[LIST]
[*]/dev/sda5 - ntfs - 11.72GB - Windows XP Pro SP3 Partition
[*]/dev/sda7 - ext3 - 7.45GB - Ubuntu OS
[*]/dev/sda8 - ext3 - 120.69 GB - Ubuntu Home
[*]/dev/sda6 - linux-swap - 1.86GB - swap partition
[/LIST]

Boot order is setup so that I first choose between Ubuntu and Windows XP (in grub), and I then choose between Windows XP and Windows 98 (in the windows boot loader).

What I want to do is resize my ubuntu home partition to make it smaller by about 20GB. I want to use this 20GB to create a new NTFS partition that Windows XP has access to (or FAT32 so Windows 98 also has access to it).

So my question is, how do I resize my home partition safely? I'm assuming once it is resized properly the formatting of the freed space will be fairly simple?

Thanks,

Stern

---

### Post by lisati on 2008-09-10
The first thing to do is defrag the Windows partitions. If you are able, make sure you backup important data.

---

### Post by sternkanz on 2008-09-10
> **lisati said:**
> The first thing to do is defrag the Windows partitions.

I do this fairly regularly anyway, but may I ask why this is necessary? I don't want to alter the existing Windows partitions in any way, I want to alter the 120GB ext3 one and with the free space create a new partition.

---

### Post by sternkanz on 2008-09-10
If (whoever is deciding to help me) needs the content of any of my system files to help me better, please let me know. I can post them here.

---

### Post by lisati on 2008-09-10
> **sternkanz said:**
> I do this fairly regularly anyway, but may I ask why this is necessary? I don't want to alter the existing Windows partitions in any way, I want to alter the 120GB ext3 one and with the free space create a new partition.

From a partitioning perspective, it helps to make sure that all the data is towards the start of the partition, should you need to shrink the partition size.
From Windows perspective it can help with the efficiency of accessing files, particularly the larger ones.

---

### Post by sternkanz on 2008-09-10
Ok, so I should defrag the ubuntu home partition? Since I am shrinking that one? How can I do this? Thank you.

---

### Post by anjilslaire on 2008-09-10
Linux partitions do not fragment, simple as that. Defragging is for NTFS & FAT partions only.

---

### Post by sternkanz on 2008-09-10
Ah, good stuff, that will probably save me some time. So back to my original question, how do I downsize the ubuntu home partition (120GB)?

---

### Post by sternkanz on 2008-09-10
Any answers? Please? I was hoping to do this soon as I really need the extra space for Windows.

---

### Post by sternkanz on 2008-09-11
bump

---

### Post by bingoUV on 2008-09-11
Boot up your live CD. Open partition editor (I think in Applications -> System Tools). Select the partition in it and resize it to a lower size.

---

### Post by sternkanz on 2008-09-12
That sounds simple enough. And that -should- not break my home partition? Would it be advisable say, to have about 40GB free on the home partition before I shave 20GB off it? Or should I leave more free just in case?

Thanks!

---

### Post by sternkanz on 2008-09-29
bump #2

---

### Post by bingoUV on 2008-09-29
> **sternkanz said:**
> That sounds simple enough. And that -should- not break my home partition? Would it be advisable say, to have about 40GB free on the home partition before I shave 20GB off it? Or should I leave more free just in case?

Thanks!

How much space you need on the home partition depends on what you store in it, right? Nobody here has any idea how much space you need, beyond, say, a minimum of 500 MB or so.

Editing partitions is always a risky operation i.e. never trust mission critical data to a single partition that you are resizing. I have never had any data loss during partition size editing, but a lot could go wrong during that time. Backup before trying this.

---

### Post by Excalibre on 2008-09-30
> **bingoUV said:**
> How much space you need on the home partition depends on what you store in it, right? Nobody here has any idea how much space you need, beyond, say, a minimum of 500 MB or so.
I think the question was whether extra free space would reduce the likelihood of errors, and I don't think it would. It's not a matter of possibly chopping off some files (gparted won't let you size a partition smaller than its contents anyway) -- it's a matter of screwing up the partition in some way that it would break entirely.


> Editing partitions is always a risky operation i.e. never trust mission critical data to a single partition that you are resizing. I have never had any data loss during partition size editing, but a lot could go wrong during that time. Backup before trying this.
Quoted for truth. I've had the same experience -- never had a problem, but I always cross my fingers anyway because it can happen.

---

