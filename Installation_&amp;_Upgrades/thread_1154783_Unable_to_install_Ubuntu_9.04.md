---
title: "Unable to install Ubuntu 9.04"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by greythorne on 2009-05-10
Need your input here,

I am trying to install onto a single hard drive which has  been partition into 3 parts. first partition is used to install windows7 RC, second is used as a backup and third will be used to install ubuntu-9.04.

But you see the problem is that when i start the installation, only a single partition is being recognised which is the entire hard drive. I do not know why the other partitions i made did not show up!. I am trying to install ubuntu into a seperate partition in the same hard drive because i need windows7 RC for testing as well.

The hard drive is an 160gig SATA-2 drive and i am using the live-CD to do the installation in this way i can atleast test before comitting.

Any help would be greatly appreciated.

Thanks.

---

### Post by apparle on 2009-05-10
you partition table seem to have gone currupt....I had the same problem
I am not the right person to help you out.
but I suggest, you post the output of

sudo fdisk -lu
sudo sfdisk -d
 
See the problem I had [http://ubuntuforums.org/showthread.php?t=1138158](http://ubuntuforums.org/showthread.php?t=1138158)
Maybe some will help you fast

---

### Post by greythorne on 2009-05-10
> **apparle said:**
> you partition table seem to have gone currupt....I had the same problem
I am not the right person to help you out.
but I suggest, you post the output of

sudo fdisk -lu
sudo sfdisk -d
 
See the problem I had [http://ubuntuforums.org/showthread.php?t=1138158](http://ubuntuforums.org/showthread.php?t=1138158)
Maybe some will help you fast

Ok.

here is the output of sudo fdisk -lu:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
135 heads, 14 sectors/track, 165387 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14b285d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
/dev/sda2          206848   167886847    83840000    7  HPFS/NTFS
/dev/sda3       167886848   271613951    51863552    7  HPFS/NTFS
/dev/sda4       271613958   312581429    20483736   83  Linux

```and for sudo sfdisk -d:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id= 7, bootable
/dev/sda2 : start=   206848, size=167680000, Id= 7
/dev/sda3 : start=167886848, size=103727104, Id= 7
/dev/sda4 : start=271613958, size= 40967472, Id=83

```

Any help from these two output?

Thanks.

---

### Post by greythorne on 2009-05-11
So none can help with these issue??

---

### Post by Crocopep on 2009-05-11
I'm having the same problem. I have a C disk with Vista.
 
I shrinked it 100 gb so I can install linux on that part.
 
But when I want to install Ubuntu it says I have no operating system on my laptop and it shows the whole harddisk.

---

### Post by greythorne on 2009-05-11
Hopefully someone here can help, im trying to transition to linux full-time. Fedora 11 preview also giving the same issue.

---

### Post by Crocopep on 2009-05-11
where is the support [this page]("http://www.whylinuxisbetter.net/items/help/index.php?lang=") is talking about?

---

