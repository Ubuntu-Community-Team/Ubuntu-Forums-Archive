---
title: "Setting up my partition table"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by dsierpin on 2006-01-24
Hello Forum!

I'm trying to install Ubuntu, Gentoo and WinXP, and I'm having a bit of a dilly getting the partition table setup.  I'm pretty sure I can have Gentoo and Ubuntu share the swap partition, but can they also share a boot partition, or does each OS have a separate one?  I'm thinking of putting the 3 OS's root files systems on primary partitions and everything else on logical partitions.  Is there any advantage to using extended partitions, or does it automatically create an extended partition when you put in the logical partitions?

Thanks in advance!

---

### Post by linuxden on 2006-01-24
dsierpin,

Your right about all linux distros being able to share the swap, however i would just install Gentoo, and ubuntu on diff parttions... as primary.

Xp you should install 1st makes everything a lot easier...

ps: make sure you install your default linux distro last so that your boot loader knows that that is the one you want last...

---

### Post by az on 2006-01-24
If you suspend-to-disk (hibernate) you will lose your data if the swap gets used by another disto - that's where your contents of your ram goes when you hibernate.

Whether a partition is primary of extended is irrelevant.

Do not share a /boot partition.  Do not share any part of the filesystem used by the package manager.

---

### Post by linuxden on 2006-01-24
Oops,

:oops:

Forgot to mention that part... I never use the hibernate features...

---

### Post by dsierpin on 2006-01-25
Hey guys-

Thanks for the helpful suggestions.  I'm still working on the installs, but I partitioned my 80 GB hard drive as follows with the GParted LiveCD:

hda1:  WinXP 9 GB NTFS
hda2:  Gentoo 9 GB ext3
hda3:  Ubuntu 9 GB ext3
hda4:  Extended Partition 53 GB
  hda5:  Swap for Gentoo 1 GB ext3
  hda6:  Swap for Ubuntu 1 GB ext3
  hda7:  Storage 52 GB FAT32

This gives me some flexibility to change things around later with GParted if I need to (i.e. adding boot partitions, resizing the storage partition to make room for other partitions etc.)  

I had to install ubuntu before Gentoo, because I needed a boot loader to be able to get into WinXP so my girlfriend could listen to her ABBA collection 	:-&  This might make things complicated down the line, but the forums haven't failed me yet.  Thanks again.

---

### Post by linuxden on 2006-01-25
Dsierpin,

EDIT:Why did you not just make it a primary partition instead of a extended? your allowed 4 are you planing on reeinstalling other distros?

also do you plan to use the hibernate to disk features and then login to another OS?? becasue if not you can save yourself 1GB of space using only 1 swap...

---

### Post by dsierpin on 2006-01-27
ubuntulifestyle-

Duly noted.  Got rid of one of the swap partitions.

As for the extended partition, if I have 4 primary then I can't have any logical right?  I might be wrong about that, I don't know :confused:  I figured if I put in the extended partition, I've got more partitions to work with for swap, storage, etc.  Is this not the case?

Also, about installing other distros: If I were to put an OS in the extended partition, could I boot to it?  I have heard of people having trouble installing OS's on logical partitions.  Thanks!

---

### Post by linuxden on 2006-01-27
Dsierpin,

There are 3 types of partitions,

"Primary" (of which you can only have 4 because windows was poorly designed, i think)

"Extended" (only allowed 1)

"Logical" (logical partitions are the ones that you put inside the extended partition)

Ie: you make an "extended" partiton to store "logical" partitions when you need more than the limited 4....

Am pretty sure about this but do wait for some confirmation on this... 

Azz?

Hope that helps...

---

### Post by breezyfox on 2006-01-27
yes you can have maximum four partion on a disk.

1. all four primary or
2. three primary and one logical ( where you can further devide extended in to logical volumes)
3. one primary for windows, one primary for linux it is all up to your needs but maximum no is four.
hope this is more clear

bz

---

### Post by breezyfox on 2006-01-27
sorry for typo mistake

2. three primary and one extended. extended you further devide in logical volumes.

bz

---

### Post by az on 2006-01-27
When I was a little kid, a hard drive could only have four partitions.  Actually, DOS could only recognise one primary partition.

You now (using a modern operating system) have up to four primary or extended partitions or any combination of both.

Each extended partition is divided up into smaller logical partitions.  I just read up that there is a maximum of 24 logical partitions per extended partition.  I am not sure about that, but I don't think I will ever need to verify that since ide technology will be obsolete before I meed more partitions than that.

So yes, you can have more than four partitions on a disk.  Who cares whether it is logical or primary -  they are all recognised the same.  Whether /dev/hda16 is primary or logical, you still mount it the same way...

---

### Post by dsierpin on 2006-01-28
> Who cares whether it is logical or primary - they are all recognised the same. Whether /dev/hda16 is primary or logical, you still mount it the same way...

So you can boot an OS from a logical partition just like you can from a primary?  

I thought the reason you could only have 4 primary partitions was that there are only 512 bytes in the boot sector, which leaves only enough room for information about 4 bootable partitions.  Maybe this means you can boot from 4 and only 4 partitions, whether they are primary or logical.  I haven't been able to find specific information about this anywhere.

Thanks again for all the help!

---

