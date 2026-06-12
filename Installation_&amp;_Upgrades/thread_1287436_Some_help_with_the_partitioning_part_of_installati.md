---
title: "Some help with the partitioning part of installation"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Dafong on 2009-10-10
Ok I finally got Gparted to run after formatting the first partition, known as C: previously, now known as /dev/sda1

During installation it has come up at step 4/7.....Use the whole disk?  I have chosen the other option, specify partitions manually.
 
It then lists my 3 partitions
 
So I edit the two partitions I don't want to use and select..."Do not use this partition" so Ubuntu will leave it alone.

When I click forward it says...

"No root file system is defined, please correct this from the partition menu"
 
Yet it doesn't offer me any sort of partition menu, or list from what menus' do exist, that speaks of or looks like it might be involved with the Root file system.
 
The menus' that are on offer are edit partition, delete partition or undo changes.  Within the Edit Partition menu is a sub menu: use as; format; mount point.  Within that submenu of "Use As" is a further submenu of file systems, Ext3 journalling; FAT16; FAT32; NTFS and the option to use it as a swap area or do not use.
 
I am not sure what I am supposed to do to create a "Root file system" or where I am supposed to do it.

---

### Post by milton1 on 2009-10-10
Under mount point select '/'

---

### Post by milton1 on 2009-10-10
You will also most likely want a partition to use as swap (linux version of virtual memory/page file)

---

### Post by Dafong on 2009-10-10
> **milton1 said:**
> You will also most likely want a partition to use as swap (linux version of virtual memory/page file)
 
So should I edit the partition and make it 2 partitions? It is 100gig all just for operating system and programs, it is not my main PC either so will only have a couple of programs loaded.
 
[quote=milton1]
**Re: Some help with the partitioning part of installation**
Under mount point select '/' [/quote]
 
Ok that isn't actually an option when I look in Mount Point it gives:
 
/dos
/windows
 
When I choose /dos it said nothing.

I will attempt to put in manually "/" so do let me know if I am not supposed to do that.

---

### Post by milton1 on 2009-10-10
It may need to be formatted first. Under the 'use as' menu, select ext3

---

### Post by Dafong on 2009-10-10
Ok that worked up to a point thanks for that.
 
if I make one of the partitions a swap drive it warns me that it will be formatting that drive.
 
I would rather it did not. It does not give me the option of partitioning /dev/sda1 any further so I can't split it into two drives to make one a swap drive.
 
Is a swap drive really essential cause I just can't format that drive.
 
 
 
Ahh also I used Ext2 since that is what it recommended, should I use Ext3 instead?

---

### Post by milton1 on 2009-10-10
Try this for a reference:

[https://help.ubuntu.com/9.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/9.04/installation-guide/i386/partitioning.html)

---

### Post by milton1 on 2009-10-10
You should be able to delete the partition you want to use, and make 2 new partitions in its place; one for root and one for swap. The swap can be small; a good rule is twice the size of your RAM.

---

### Post by Dafong on 2009-10-10
> **milton1 said:**
> You should be able to delete the partition you want to use, and make 2 new partitions in its place; one for root and one for swap. The swap can be small; a good rule is twice the size of your RAM.
 
Once I knew it was possible, I tried deleting the partition and that gave me the 'freespace' to create 2 new partitions.

Installation underway, thanks for the help.

---

### Post by milton1 on 2009-10-10
You are welcome. Good luck with the rest.

---

### Post by Dafong on 2009-10-10
> **milton1 said:**
> You are welcome. Good luck with the rest.
 
Well now it seems to be stuck on 99% installation saying:
 
Running post-installation triggers libc6
 
Been stuck on that for about 5mins now.

---

