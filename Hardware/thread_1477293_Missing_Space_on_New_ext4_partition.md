---
title: "Missing Space on New ext4 partition"
date: 2010-05-08
forum: Hardware
---

### Post by Hacker3141 on 2010-05-08
I recently attempted to install Chromium OS to my external USB hard drive. It didn't boot properly, so I decided to reformat the disk to two 250GB partitions, one NTFS and one ext4. I opened up the ext4 partition to find a folder called 'lost+found' and 11.8GB used. I removed the folder, however, the space is still missing. Is there a way to get rid of this problem?

---

### Post by Nohajc on 2010-09-13
Yes, I have the same problem. Just bought a new internal 2TB drive and after creating single ext4 partition it reports **90 GB** used! That can't be normal I think.

---

### Post by Elfy on 2010-09-13
It is normal - 5% of the drive is reserved.

You can use tune2fs to change the amount that is reserved.

For example if the drive in question was sde1 and you wanted to change it to 1%

sudo tune2fs -m 1 /dev/sde1

2% would be 

sudo tune2fs -m 1 /dev/sde1

[https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20%28Optional%29](https://help.ubuntu.com/community/InstallingANewHardDrive#Modify%20Reserved%20Space%20%28Optional%29)

---

### Post by Nohajc on 2010-09-13
Thanks for your information.
I would like to ask though how is it with the overall efficiency when I start decreasing the reserved space?
How exactly is this reserved space being used?

---

### Post by Elfy on 2010-09-13
From my understanding it is only likely to be used when you're running out of space 

> reserved for the super-user (root) so that the operating system can still write to the disk even if it is full. However, for disks that only contain data, this is not necessary.

---

### Post by Nohajc on 2010-09-13
Thank you, that's exactly what I wanted to hear. 
I was able to completely free up the reserved space by setting *tune2fs -m* to 0%.
Worked like a charm!

---

