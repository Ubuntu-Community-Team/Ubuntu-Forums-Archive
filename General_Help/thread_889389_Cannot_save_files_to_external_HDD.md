---
title: "Cannot save files to external HDD"
date: 2008-08-14
forum: General Help
---

### Post by MeanStreak on 2008-08-14
Hi,

I've recently formatted my external HDD to ext3 however I now cannot copy files to it for backup purposes - please help! How do I change permissions on my HDD so I can copy files to it?

---

### Post by MrFSL on 2008-08-14
This has been answered many places so I will be brief. 

Identify where it is mounted. - The command 'cat /proc/mounts' might be helpful

Identify its block device location. - The command 'cat /proc/partitions' might be helpful

lets pretend out device is /dev/sdb1 mounted at /media/disk-1

we should check the permission on these:
```
ls -l /dev/sdb1
ls -ldp /media/disk-1
```

change permissions using chmod - for more information type:
```
man chmod
```

Hope this helps.

---

### Post by hyper_ch on 2008-08-14
or rather change ownership to your user instead of chmodding
```

sudo chown -R USERNAMER:USERNAME /path/to/external/drive

```

---

### Post by coffeecat on 2008-08-14
Here's another way. The advantage of this is that if you use more than one USB drive, this one may get mounted to a different mountpoint next time you use it if the other one is already in use. The disadvantage is that you have to make a special folder in which you can work, and this is not so elegant. 


1 Find the mountpoint. I'll assume like an earlier poster that it's /media/disk-1.

2 Create a special folder.

```
sudo mkdir /media/disk-1/myfolder
```3 Change permissions for the folder.

```
sudo chown *yourusername*: /media/disk-1/myfolder
```Obviously, put your user name instead of *yourusername*, and don't forget the trailing colon.

You'll now have a folder that you can drag and drop files into, or delete and modify them whenever you mount the drive.

---

### Post by hyper_ch on 2008-08-14
won't work... with the mounting the permissions and ownership of that created folders will be overwritten.

---

### Post by coffeecat on 2008-08-14
> **hyper_ch said:**
> won't work... with the mounting the permissions and ownership of that created folders will be overwritten.

I suggest you try it. It works for me. Mounting the external drive will **not** change the ownership/permissions of a folder already created within the root of the filesystem of the external drive. Neither will it change permissions of files saved within the folder.

---

### Post by MrFSL on 2008-08-14
> **hyper_ch said:**
> or rather change ownership to your user instead of chmodding
```

sudo chown -R USERNAMER:USERNAME /path/to/external/drive

```

or rather

```
sudo chown -R USERNAME:GROUPNAME /path/to/external/drive
```

---

### Post by MeanStreak on 2008-08-17
Yes, thank you both for you help - I now have the appropriate write access.

---

