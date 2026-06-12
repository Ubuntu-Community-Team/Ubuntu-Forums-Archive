---
title: "move folders to other drive"
date: 2019-01-22
forum: Hardware
---

### Post by PaulNL on 2019-01-22
Hello All,

I have a new laptop with two harddisks one SSD en one normal now i had the idea to move the document, image music folders to the other bigger harddisk end made it wit symbolic links but the problem is that after starting up it not work like i wan't it to.

When i start up de the system does nothing with the folders until i open a folder on the second harddisk than it works. How can i get de folders on the second disk and get it working on boot.


Paul

---

### Post by Dennis N on 2019-01-22
> **PaulNL said:**
> Hello All,

I have a new laptop with two harddisks one SSD en one normal now i had the idea to move the document, image music folders to the other bigger harddisk end made it wit symbolic links but the problem is that after starting up it not work like i wan't it to.

When i start up de the system does nothing with the folders until i open a folder on the second harddisk than it works. How can i get de folders on the second disk and get it working on boot.


Paul

You can automatically mount the partition that contains those folders on startup by adding an line to your **/etc/fstab** file. Here is an example from my computer:

```
UUID=0dcd0e58-98ec-44e2-aab7-2b4e35144a56 /mnt/data ext4 defaults,noatime 0 2
```

when its added to /etc/fstab, my computer mounts the partition with the file system UUID. Mine mounts it at the folder **/mnt/data**.  You should create this mount point folder as well. You could then have symbolic links to a folder by using a path through the mount point to your folder.

Find the UUID of a partition by using command **lsblk -f** in the terminal.

---

### Post by sisco311 on 2019-01-22
If you don't want to edit the fstab file manually, then you can use disks (gnome-disk-utility).

 [https://www.makeuseof.com/tag/manage-ubuntu-hdd-disk-utility/](https://www.makeuseof.com/tag/manage-ubuntu-hdd-disk-utility/)

---

