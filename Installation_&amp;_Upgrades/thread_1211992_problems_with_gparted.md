---
title: "problems with gparted"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by hogu on 2009-07-13
I have /dev/sda1 - NTFS, 70gb
/dev/sda3 - extended which houses /dev/sda5 and /dev/sda6
/dev/sda5 - ext3 /
/dev/sda6 -ext3 swap
/dev/sda2  NTFS HP recovery

originally /dev/sda1 was 120 gb, I wanted to shrink it to 70 gb to make more room for my /dev/sda5.  I shrunk it, everything was ok.

I used gparted from the ubuntu 9.04 live cd and made the /dev/sda3 and /dev/sda5 big.

gparted quit in the middle ( I'm not sure where, I ran it overnight).  

I can boot into my old ubuntu install fine, except the file system on /dev/sda5 is still small(27gb, 9gb used)

when I run gparted, it thinks the stretch was successful, and that /dev/sda5 is now 70gb, with 51 gb used.  I think gparted must've quit while it was moving data around, but the new fs didn't get created properly.  

So, the question is, how do I fix this.

should I 

mount -t ext3 /dev/sda5 /mnt/ubuntu/
cp -rf /mnt/ubunbtu/* /mnt/backup

then recreate the filesystem on /dev/sda5, and copy all my files back over? will ubuntu still load up ok? thanks in advanced.

---

### Post by az on 2009-07-13
I don't really understand what is where by your description, so I can't say what will happen if you copy and recreate a filesystem on sda5

But it may be that the partition is resized, but the filesystem on it is still the old size.  If that's the case, then you should be able to resize the filesystem if it's unmounted.

---

### Post by hogu on 2009-07-13
sorry, I tried to edit my description to make it clearer

how do I resize the file system? with gparted?

before gparted I had a 27gb partition, with 9gb of data
now gparted says I have a 71gb partition, with 51 gb of data

so I'm not sure what gparted will do, given it thinks I have all this extra data I don't really have.

Thanks

---

### Post by az on 2009-07-13
Where is your Ubuntu instaled?  Sda5 or another drive?

You resize an ext3 partition using resize2fs

man resize2fs

---

### Post by hogu on 2009-07-13
yes /dev/sda5

Thanks for the feedback, I'll try resize2fs

I looked at the man page just now, and it doesn't mention anything about the partition, other than the fact that it has to be big enough - do I need to do anything to make sure that resize 2fs puts it in the right place?

if I choose a new size that is about the size of the partition, i'll be in good shape?

thanks.

---

### Post by hogu on 2009-07-13
thanks! resize2fs did it perfectly!

---

### Post by vladk2k on 2009-09-17
Hi, I have a similar problem and I didn't want to start a new thread.

I have a 1TB external drive (WD My Book Essential) which had a FAT32 partition with some tools. I've shrunk that partition to 2GB and made some new partitions for my router (0.5 GB swap, 1GB for ipkg and the rest - roughly 950GB - for "storage").
Now, my router is a bit fussy and kept ignoring the fstab and mounted the FAT32 partition instead of the "storage" partition.
I've put the drive on my desktop (running ubuntu 9.04) and ran gparted to do the following:
[list][*]delete all partitions except the "storage" partition
[*]move the "storage" partition to the front
[*]recreate the partitions at the end of the drive.[/list]

I left it to do this overnight. In the morning, it was still copying the storage partition (over 400GB copied, more than my data anyway). An hour or two later, I checked it and it was gone. No gparted, no error message, no nothing (all my other running applications were there, so the system didn't reboot).
Now fdisk -l says something that is correct - 1 partition, starts at 1 and has 950 GB size, type 83.
Unfortunately, mounting it results in the contents of the FAT32 partition being shown (and gparted sees it as FAT32 partition as well). Running e2fsck says the superblock is invalid. I've tried the standard 8193, 16384 and 32768 superblocks but all of them resulted in "Bad magic number in super-block while trying to open /dev/sdb4".

Is there any way to recover my data now?

---

### Post by vladk2k on 2009-09-18
Well, seems like once again I fixed it by myself.

gparted didn't move any actual data, it only screwed the partition table, which I was able to recover using **gpart**

---

