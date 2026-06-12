---
title: "File transfers, ubuntu to xp?"
date: 2008-08-19
forum: General Help
---

### Post by connor da og on 2008-08-19
When in xp, isit possible to transfer files from my ubuntu partion, i no you can do it whilst in ubuntu, but ubuntu doesnt show up in xp, basicly, i want to transfere files from my ubuntu partion to my xp


please & thank you :P

---

### Post by Saggy Peanuts on 2008-08-19
What i would do is create a partition using FAT. Something small, enough to hold the files you want to transfer. Then when in Ubuntu, transfer those files into the partition. Reboot into XP, and transfer the now visible FAT partition files into the XP partition.
The only problem you have now is whether to shrink the linux partition or XP partition to create the new partition.

What I have on one of my PCs is the XP partition, the Ubuntu parition, and a seperate Media parition for all my music and videos which is shared with both.

Hope that helps

---

### Post by connor da og on 2008-08-19
> **Saggy Peanuts said:**
> What i would do is create a partition using FAT. Something small, enough to hold the files you want to transfer. Then when in Ubuntu, transfer those files into the partition. Reboot into XP, and transfer the now visible FAT partition files into the XP partition.
The only problem you have now is whether to shrink the linux partition or XP partition to create the new partition.

What I have on one of my PCs is the XP partition, the Ubuntu parition, and a seperate Media parition for all my music and videos which is shared with both.

Hope that helps

Thanks thats a very good idea, and i have no idea why i didnt think of that :D.

---

### Post by Saggy Peanuts on 2008-08-19
I dont know what reason you might have to transfer files over. But perhaps it wouldn't be a bad idea to keep the partition when finished. I use one similar for my music and videos so that both partition can access it.

---

### Post by connor da og on 2008-08-19
> **Saggy Peanuts said:**
> I dont know what reason you might have to transfer files over. But perhaps it wouldn't be a bad idea to keep the partition when finished. I use one similar for my music and videos so that both partition can access it.
Yh I'm planing to, gona nick 10gigs of my xp partion hehe

---

### Post by doas777 on 2008-08-19
> **connor da og said:**
> When in xp, isit possible to transfer files from my ubuntu partion, i no you can do it whilst in ubuntu, but ubuntu doesnt show up in xp, basicly, i want to transfere files from my ubuntu partion to my xp


please & thank you :P

it's my understanding that you can write to NTFS media from Ubuntu now. what is preventing you from just mounting your XP partition from ubuntu, and copying your files?

good luck,
franklin

---

### Post by trevelyan on 2008-08-19
you dont have to go through the trouble of partitioning your disks.. [just download ext2fsd-0.46a.exe from here]("http://ext2fsd.sourceforge.net/projects/projects.htm") and install it in windows XP. it's a driver to let you see see the ubuntu partition from XP.

---

### Post by connor da og on 2008-08-19
> **doas777 said:**
> it's my understanding that you can write to NTFS media from Ubuntu now. what is preventing you from just mounting your XP partition from ubuntu, and copying your files?

good luck,
franklin

Is that a new feature in hardy?, I'll be sure to give it a try before i partion my hd tho, thanks for the tip

---

### Post by trevelyan on 2008-08-19
thought i would also let you know how to automount your volumes at startup in case you dont know.
```
**Steps to enable auto-mount of hard drives at startup of Ubuntu**

before you start make sure all other partitions (except file system of course) are unmounted

Step 1
open Synaptic Package manager
search for &#8220;NTFS-config&#8221;
Install the software

Step 2
Open the configuration tool by going to Applications >  System Tools > NTFS Configuration Tool
select the hard drives you want to enable. Also enable read/write support for both internal and external devices.

(this creates lines in your fstap file with the new configuration for the hard drives.)

Step 3
Reboot your computer and verify that the disks auto-mounted.

```

---

### Post by connor da og on 2008-08-19
> **trevelyan said:**
> thought i would also let you know how to automount your volumes at startup in case you dont know.
```
**Steps to enable auto-mount of hard drives at startup of Ubuntu**

before you start make sure all other partitions (except file system of course) are unmounted

Step 1
open Synaptic Package manager
search for “NTFS-config”
Install the software

Step 2
Open the configuration tool by going to Applications >  System Tools > NTFS Configuration Tool
select the hard drives you want to enable. Also enable read/write support for both internal and external devices.

(this creates lines in your fstap file with the new configuration for the hard drives.)

Step 3
Reboot your computer and verify that the disks auto-mounted.

```

Thanks, but i did that as soon as i installed ubuntu :D | cheers for your help tho!

---

