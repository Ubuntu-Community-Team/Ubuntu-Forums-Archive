---
title: "after resize hd with qtparted usplash doesn't work good"
date: 2008-11-02
forum: Hardware
---

### Post by aleomark on 2008-11-02
Hi, I have a compaq presario f755la, and today i wanted give more space (5gb) to the ubuntu partition (EXT3) from a document partition (NTFS), my partitions used to be like these:

1-NTFS 15gb with windows XP
2-NTFS 83gb with documents and stuff
3-SWAP 1gb
4-EXT3 13.5gb with ubuntu 8.04

and now are:

1-NTFS 15gb with windows XP
2-NTFS 78gb with documents and stuff
3-SWAP 1gb
4-EXT3 18.5 gb with ubuntu 8.04

I did it with gtparted live cd, and everything when fine, with a litle problem, the usplash works bad, at start it shows ok, moving from left to right and reverse, but after a second or 2, it doesn't show the progressing bar and the letters shows instead.

How can i correct this, and have the usplash working again?

PD: in that process i did manipulate the swap partition, and tried this but didn't work:

1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart

some help, please

---

### Post by IEKnight on 2008-12-21
> **aleomark said:**
> 
PD: in that process i did manipulate the swap partition, and tried this but didn't work:

1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart

some help, please

1. Make sure you have the initramfs-tools update
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
**3a. make sure that the UUIDs from all other partitions that are listed in /etc/fstab match their corresponding UUIDs in from step 2**
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -u
6. Restart

It's not just the swap - everything has to match.

Since i've only had this problem with my swap, I may be missing an extra step, but nevertheless I hope this helps.

---

