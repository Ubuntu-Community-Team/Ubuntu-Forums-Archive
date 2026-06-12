---
title: "Formatting HDDs"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by deamon_knight on 2007-11-13
I have Gutsy running on a 160GB SATA HDD. Everything is working fine, but I have an 80GB IDE HDD is want to add for additional space. I has previously used this drive for some linux tests and it was formatted in ext3 with a swap partition.

It connects properly and I could mount it and read the old filesystem. I tried to reformat the ext3 partition so it would be blank. Having done this I can mount the drive and read the 72GB filesystem, howeverr I cannot change the name of the volume. I can see a single directory that says lost and found, but I can't create new directories or copy data to the drive. What am I doing wrong?

---

### Post by taurus on 2007-11-13
Currently, root is the owner of the mount point of that drive.  So, if you want to write to it without using sudo, then you need to change the ownership from root to your login name.  _Assuming_ the mount point of that drive is /media/sdb1 and your login name is **knight**, do

```
sudo chown -R **knight**:**knight** /media/sdb1
ls -la /media
```

---

### Post by deamon_knight on 2007-11-13
Thanks Taurus, that got me access to the drive. Now the disk name is "computer:///73.5%2520GB%2520Volume.drive" or 73.5GB volume and the partion (or volume?) name is drive. Any way to change this?

Also, those commands output this

<CODE>
jay@linuxdeamon:~$ sudo chown -R jay:jay /media/disk
jay@linuxdeamon:~$ ls -la /media
total 20
drwxr-xr-x  4 root root 4096 2007-11-13 22:19 .
drwxr-xr-x 21 root root 4096 2007-11-01 01:22 ..
lrwxrwxrwx  1 root root    6 2007-11-01 01:09 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-11-01 01:09 cdrom0
drwxr-xr-x  3 jay  jay  4096 2007-11-13 17:04 disk
-rw-r--r--  1 root root   44 2007-11-13 22:19 .hal-mtab
-rw-------  1 root root    0 2007-11-13 16:59 .hal-mtab-lock
<END CODE>

now, that leaves me with more questions, What were those commands you told me to execute, and how do I interpret those results?

Thanks

---

### Post by taurus on 2007-11-13
The first one,** sudo chown -R jay:jay /media/disk**, to change the owner/group of /media/disk from root to your login name, jay, so you can write to it anytime you want. 

The second command, **ls -la /media**, just displayed the contain of of /media so you can check to see if jay is really the owner of disk now.

---

