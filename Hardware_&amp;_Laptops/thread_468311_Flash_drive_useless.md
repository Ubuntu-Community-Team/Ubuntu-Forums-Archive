---
title: "Flash drive useless?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by ryanVickers on 2007-06-08
My friend had this 256Mb flash drive and it wasn't working, so he wanted me to take a look at it.  Well, there was no partition on it, so that was the problem I thought, easy to fix right!?

Wrong!
There is really something wrong with it, not just windows corrupting it own stupid FAT filesystem like I thought.  I tryed a mkfs command from the command line to get a better report than "could not create disk label" (needed to have any partitions)) and the out put was this:
> Warning: could not erase sector 2: Attempt to write block from filesystem resulted in short write
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
64768 inodes, 259072 blocks
12953 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
32 block groups
8192 blocks per group, 8192 fragments per group
2024 inodes per group
Superblock backups stored on blocks: 
        8193, 24577, 40961, 57345, 73729, 204801, 221185

Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block from filesystem resulted in short write
Writing inode tables:  0/32
Could not write 8 blocks in inode table starting at 261: Attempt to write block from filesystem resulted in short write


Is there something phisically wring with it?  Like a bad sector or something, or do I just need more powerful tools?  No rush, and there is nothing on it, so no worries, but I'd really like to know how this happened and maybe how to fix it/or is it just garbage?

---

### Post by stchman on 2007-06-08
> **ryanVickers said:**
> My friend had this 256Mb flash drive and it wasn't working, so he wanted me to take a look at it.  Well, there was no partition on it, so that was the problem I thought, easy to fix right!?

Wrong!
There is really something wrong with it, not just windows corrupting it own stupid FAT filesystem like I thought.  I tryed a mkfs command from the command line to get a better report than "could not create disk label" (needed to have any partitions)) and the out put was this:


Is there something phisically wring with it?  Like a bad sector or something, or do I just need more powerful tools?  No rush, and there is nothing on it, so no worries, but I'd really like to know how this happened and maybe how to fix it/or is it just garbage?

Fire up gparted and select the flash drive.  There you can delete the partition and make a FAT32 partition on the drive.  Select FAT32 as it is able to be read by most OSs.  There may actually be something wrong with the flash drive.  I had a 256MB flash drive that would always corrupt data I put on it.

---

### Post by ryanVickers on 2007-06-08
> There you can delete the partition and make a FAT32 partition on the drive.
I said that there was no partition right here: :p
> Well, there was no partition on it, so that was the problem I thought, easy to fix right!?

But thanks for the idea.  The thing is to make partitions it needs something called a disk label and it can't make one due to these errors:
> Warning: could not erase sector 2: Attempt to write block from filesystem resulted in short write
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
64768 inodes, 259072 blocks
12953 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
32 block groups
8192 blocks per group, 8192 fragments per group
2024 inodes per group
Superblock backups stored on blocks:
8193, 24577, 40961, 57345, 73729, 204801, 221185

Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block from filesystem resulted in short write
Writing inode tables: 0/32
Could not write 8 blocks in inode table starting at 261: Attempt to write block from filesystem resulted in short write
Any hardware/partition expert notice this as familiar (to a bod thing maybe...)?

---

### Post by 444 on 2007-06-08
I would say it's toast. Even if it's 'just' bad sectors, there aren't supposed to be any on flash drives, bad sectors are handled by the drive's controller chip. If the start showing up it means there's a huge number of them, and more to come soon.

I use this to test drives:
dd if=/dev/whatever of=/dev/null

And if the result is 'Input/output error' or some such, then you know something's physically wrong with the drive.

---

### Post by ryanVickers on 2007-06-08
Yup, it's messed up bad!  Thanks for your help making sure!  He didn't seem to mind if it didn't work anymore, just wanted me to take a look at it to make sure it was/wasn't recoverable.

---

