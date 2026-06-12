---
title: "Partitioning"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Adrian0 on 2009-07-22
Am fairly new to Linux.  I installed Ubuntu 9.04 to my laptop using live CD, taking the whole disk. To protect working files, I have since successfully created a new partition, in Ext 2, using a live CD of GParted. 

However, I get the message that 'I am not the owner (which is 'root')!  How do I take ownership, so I can re-name the partition, create a new /Home folder and save to this, rather than the folders in the first partition?  Do I need to re-format the new partition to FAT, as my laptop is also on a Windows network?

---

### Post by merlinus on 2009-07-22
If you want to share the partition with windows, best to format is as ntfs.  I would not mount it as /home, however; /data or /media/data would be better, so as not to interfere with your ubuntu /home.

In any event, ext3 or ext4 is far superior to ext2.

---

### Post by Adrian0 on 2009-07-22
> **merlinus said:**
> If you want to share the partition with windows, best to format is as ntfs.  I would not mount it as /home, however; /data or /media/data would be better, so as not to interfere with your ubuntu /home.

In any event, ext3 or ext4 is far superior to ext2.


Thank you! I intend to rename as /DATA. However, I get the message "You are not the owner ('root')".  How do I take ownership to incorporate it into the structure?

---

### Post by merlinus on 2009-07-22
```
gksu nautlilus
```

Navigate to the mountpoint, rightclick, properties, permissions.  Make sure the partition is unmounted so your changes will stick.

---

