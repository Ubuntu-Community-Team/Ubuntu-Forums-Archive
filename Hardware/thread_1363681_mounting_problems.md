---
title: "mounting problems"
date: 2009-12-24
forum: Hardware
---

### Post by jcipale on 2009-12-24
I have just installed a 2nd hdd in my workstation. The drive is found at /dev/sdb. I partitioned the drive into two 150GB locations at sdb5/sdb6 using Gparted.

Here is the issue. WHen I attempt to mount the partitions, I use the following command (manually for now):
[INDENT]%mount -t ext3 /dev/sdb5 humboldt:/penguin1
[/INDENT]
For some reason, I am getting the following error:
[INDENT]mount: mount point humboldt:/penguin1 does not exist
[/INDENT]The mountpoint exists and is listed as such:
[INDENT]drwxr-xr-x   2 root root  4096 2009-12-24 14:07 penguin1

[/INDENT]I have never seen this failure before when attempting to mount/install extended HDD storage in FC, SuSE or even 9.1(?) ubuntu. ANy ideas?

Thanks.

Joe

---

### Post by taurus on 2009-12-24
Is the mount point penguin1 under root (/penguin1)?

```
sudo mkdir /mnt/penguin1
sudo mount -t ext3 /dev/sdb5 /mnt/penguin1
df -h
```

---

### Post by Some Penguin on 2009-12-24
> **jcipale said:**
> %mount -t ext3 /dev/sdb5 humboldt:/penguin1
For some reason, I am getting the following error:[INDENT]mount: mount point humboldt:/penguin1 does not exist
[/INDENT]The mountpoint exists and is listed as such:[INDENT]drwxr-xr-x   2 root root  4096 2009-12-24 14:07 penguin1
[/INDENT] You told it to mount it at a directory called "humboldt:/penguin1", not /penguin1.

---

