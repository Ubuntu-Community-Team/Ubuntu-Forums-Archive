---
title: "File system for external hard disk drive"
date: 2015-01-31
forum: Hardware
---

### Post by Shiryu on 2015-01-31
I will buy an external HDD.
Is ext4 the best file system to use?

---

### Post by SeijiSensei on 2015-01-31
If you intend only to use it with Linux, then yes.  If you want to be able to use it with Windows systems as well, you'll need to format it with FAT32 or NTFS.  FAT32 has a maximum file size of 4 GB, if that matters.

---

### Post by Shiryu on 2015-02-01
It will be used only with my computers. If I need to send files to a Windows PC, the data will never be more than... 2GB.
Can I disable all permissions in an ext4 partition?
I want to connect and disconnect the HDD like a USB flash drive without any additional effort.

---

### Post by SeijiSensei on 2015-02-01
If the users and groups on the various machines are identical (e.g., user chris has UID 1000, tina has 1001, etc.), then you can move the drive among machines and preserve permissions.  You can do this by using a common /etc/passwd and /etc/group file on all the machines.

It's easiest if you're going to be the only user.  In that case, just plug the drive in after you log in, and it will be mounted as /media/username/something with your permissions.

---

### Post by Mark Phelps on 2015-02-02
>  If I need to send files to a Windows PC,

In that case, format it FAT32 or NTFS -- since both Windows and Linux can read/write both filesystems.

---

### Post by leclerc65 on 2015-02-02
> **Mark Phelps said:**
> In that case, format it FAT32 or NTFS -- since both Windows and Linux can read/write both filesystems.
I thought he said SEND files, not sharing the same partition, in that case it doesn't matter whether it's NTFS or EXT4.
In my experience Windows and Linux don't co-exist peacefully. Go for EXT4.

---

### Post by weatherman2 on 2015-02-02
I would take the word "send" figuratively, not literally in the network sense, as the OP did not mention file sharing.  If the OP means "share over the network" then clarification would help.

Otherwise, I'd use NTFS.  Well supported in every OS.  ext4 is not.

---

### Post by Shiryu on 2015-02-04
The external hard drive does not need to support Windows, because I can use USB flash drive to transfer files between my PCs and Windows PCs.

My problem is the annoying permissions. The users will be different. I want to use the device without root. The use should be easy and simple.
Is btrfs good? It is new, I have never used it.

---

### Post by weatherman2 on 2015-02-04
Use ext4.  Right after you create the ext4 partition, use a root shell and change the permissions to 777:

```
sudo chmod -R 777 /media/ubuntu/YOUR-EXT4-PARTITION-NAME
```

This gives read-write permissions to all types of users (yourself, your groups, and "others").

Then you will never have permissions issues again.

---

