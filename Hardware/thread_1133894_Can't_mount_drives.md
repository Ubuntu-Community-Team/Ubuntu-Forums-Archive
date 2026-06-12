---
title: "Can't mount drives"
date: 2009-04-23
forum: Hardware
---

### Post by jonnytabpni on 2009-04-23
Hi folks,

I hope this is in the correct section.

I'm trying to mount a new partition I created. It is located at /dev/sdb1

When I do mount /dev/sdb1 /home/vmail
everything seems ok. Then I add some test files using nano.

However if I use umount, the files still remain! And, if I remount the partition to a different location, the fiels arn't there proving that the files arn't being created on the new drive.

What's wrong?

Thanks for your help

---

### Post by Mark_in_Hollywood on 2009-04-23
> **jonnytabpni said:**
> Hi folks,

I hope this is in the correct section.

I'm trying to mount a new partition I created. It is located at /dev/sdb1

When I do mount /dev/sdb1 /home/vmail
everything seems ok. Then I add some test files using nano.

However if I use umount, the files still remain! And, if I remount the partition to a different location, the fiels arn't there proving that the files arn't being created on the new drive.

What's wrong?

Thanks for your help

Please post the output of /etc/fstab

Let us start there. It will show info about sdb1

do

alt-F2

gksudo gedit /etc/fstab

---

### Post by drs305 on 2009-04-23
You are correct in your analysis that the files are probably not being written to /dev/sdb1 and instead are being saved in the /home/vmail folder.

Since you may not have this in fstab, here are some other questions to answer if you don't. 

Does /home/vmail exist and if so, who owns it?  Run:  **ls -la /home**
What is the format of /dev/sdb1?  **sudo fdisk -l | grep "/dev/sdb1"**
After you run the "mount /dev/sdb1 /home/vmail", run "**mount**". Is sdb1 mounted?

---

