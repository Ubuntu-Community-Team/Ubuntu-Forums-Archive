---
title: "Identical UUIDs for FAT32 partitions problem"
date: 2008-08-09
forum: General Help
---

### Post by xenomorph99 on 2008-08-09
Hi,

I recently reinstalled 8.04.1 but have found that I have two identical UUIDs for two FAT32 partitions. 


blkid yields:

/dev/sda1: LABEL="/" UUID="16766752-8b09-4a53-be00-937fe6ffcca0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" LABEL="SWAP-sda5" UUID="56d28b19-5c99-4c40-a9bc-5b75800d564d" 
/dev/sda6: LABEL="DISK1_3" UUID="4841-A185" TYPE="vfat" 
/dev/sda7: LABEL="DISK1_1" UUID="4841-A185" TYPE="vfat" 
/dev/sda8: LABEL="DISK1_2" UUID="4841-A186" TYPE="vfat" 
/dev/sda9: LABEL="DISK1_4" UUID="4841-A188" TYPE="vfat" 

I haven't done any dds on these partitions, so I don't understand why the UUID is the same.

So,
Is there a bug?

Can I change the UUID of a FAT32 partition easily?


On an alternative note, is it possible to refer to UUIDs in Grub?

TIA,
X

---

### Post by phidia on 2008-08-09
That's odd that they're identical since that's part of the reason for going to UUID (unique drive #'s) 
Maybe this [Ubuntu wiki guide]("https://help.ubuntu.com/community/UsingUUID") will be helpful? As to grub I believe if you look that grub does use the UUID label.

---

### Post by xenomorph99 on 2008-08-09
Thanks for the reply.

I couldn't see anything there that would allow me to set a new UUID for the FAT32 partition, though.

Is it possible to do this (change it)?

TIA,
X

---

### Post by phidia on 2008-08-09
It looks like there's a post [here]("http://ubuntuforums.org/showthread.php?t=869801") related to that. Hope that's useful.
Although it may not be a simple process.

---

