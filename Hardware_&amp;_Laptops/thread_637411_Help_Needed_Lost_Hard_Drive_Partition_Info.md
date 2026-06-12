---
title: "Help Needed: Lost Hard Drive Partition Info"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by Existentialist on 2007-12-10
So to start, I'm running a dual boot with xp/ubuntu7.10 on the same hd, and have 3 storage hds which are formated ntfs with single partitions.  I was copying a file in ubuntu today from the shell and accidentally did this as root:

>cp file.txt /dev/sdd1
(I should mention you probably do not want to try this)

Now that hd shows up as having one large empty non-formatted partition in windows, and when I try to mount the drive in ubuntu using:

>sudo mount /media/sdd1  (this is how it is identified in fstab)

I get an error saying something along the lines of, can not find device by UUID=(the UUID from fstab).

I know the data is still there, I believe I just wrote the file to the block device and the partition is not identified anymore.  I'm wondering if there is an easy solution to undo this mistake, or if I should just run a file recovery program to recover the data from the partition?

Thanks for any assistance.

---

### Post by tommcd on 2007-12-11
See this page:
[https://help.ubuntu.com/community/UsingUUID?highlight=%28uuid%29](https://help.ubuntu.com/community/UsingUUID?highlight=%28uuid%29)
Run the command to find out your UUIDs:
sudo /sbin/vol_id -u /dev/sdaX (adjust the /dev/sdaX part to point to the problem drive).
Then check you fstab "cat /etc/fstab" to see if the UUID is the same for that drive. If it is not the same then correct it in fstab and see if you can mount it
EDIT: you can also run "ls /dev/disk/by-uuid -lah" to find out the UUID.

---

### Post by Existentialist on 2007-12-11
Thanks for the reply.

I tried both of those and greping for it in /dev/disk/by-uuid returns nothing while 
>/sbin/vol_id -u /dev/sdd1  returns:
/dev/sdd1: unknown volume type

One thing I did notice is that when I run fdisk, the drive still shows up as having an NTFS partition on it and seems to be mounted and writable in linux.  I can cd in to it, but have not tried writing anything because I would prefer not to ruin any chance of recovering the data in tact.  It seems like I might have overwritten the System Volume Information.  Does anybody know if this contains the partition information only or also the Master File Table for NTFS?  I would imagine that if the MFT was overwritten I'll need use data recovery software.

---

### Post by vanadium on 2007-12-11
If the most important is to recover the data, then I would try mounting the disk read-only (you indicate you could do that), eventually with the force option if necessary, and recover the data. After that, the partition can be recreated and reformatted. I do not now of a way of recovering the file system data you presumably overwrote.

---

### Post by Existentialist on 2007-12-11
Thought I would update this in case anybody else has an issue with this.  I installed testdisk, and used the option to recover the NTFS boot sector.  Everything is back to normal now and it only took a min to fix.  The drive I was attempting to fix only had a single partition on it, so I can't say that this method would work in all cases.

Thanks for the replies.

---

### Post by vanadium on 2007-12-11
Thank you for reporting this back for us to learn. You fixed it wonderfully!

---

