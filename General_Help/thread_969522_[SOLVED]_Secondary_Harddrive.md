---
title: "[SOLVED] Secondary Harddrive"
date: 2008-11-03
forum: General Help
---

### Post by Fred_E _krugar on 2008-11-03
I have been Using Ubuntu for a while now. But I am now having a problem.

I want to use my second HD for just storage (I used to use it as a second OS). I cannot seem to make any folders or transfer things to the second hard drive, it says I do not have permission. 

How do I make it available for anyone using the comp??

Thx for the help.

---

### Post by drs305 on 2008-11-03
Generally, you would change the ownership of its mount point to yourself and then give everyone access.

If the device is mounted on /media/mymountpoint, for example, the command would be:
```

sudo chown -R *yourusername:* /media/mymountpoint
chmod -R 777 /media/mymountpoint

```

This would work for an ext3 partition. fat32 and ntfs partitions act a bit differently.

---

### Post by drs305 on 2008-11-03
Self-reported as double-post.

Generally, you would change the ownership of its mount point to yourself and then give everyone access. This would work for an ext3 partition. (fat32 and ntfs partitions would act a bit differently.)

If the device is mounted on /media/mymountpoint, for example, the command would be:
```

sudo chown -R *yourusername* /media/mymountpoint
chmod -R 777 /media/mymountpoint

```

This would work for an ext3 partition. fat32 and ntfs partitions act a bit differently.

---

