---
title: "[How-To] Recover Data From Seagate BlackArmor Drives"
date: 2010-11-22
forum: Hardware
---

### Post by ircmaxell on 2010-11-22
I ran into an issue where a Seagate Blackarmor 220 unit went bad (the device would not boot properly).  So I needed to recover the data from the raw hard drives themselves (the backup appeared not to be working).  I spent about an hour trying to figure out how to recover them as there was no information to be found via Google.  So I'm posting it here...

To start, connect the SATA drive to the computer.  I used a USB converter, but you can connect it directly.

Second, verify which drive it is:

```
ls /dev/sd*
```

It'll likely be the highest lettered drive (sdb for me).  It should have 4 partitions (sdb1 -> sdb4).  The data partition is the last (sdb4 for me)...

Now, the drive uses mdadm for raid, and ext3 for the filesystem.  So first, let's setup mdadm for the device:

```
sudo mdadm --auto-detect
```

Now, let's find the mapper:

```
ls /dev/mapper
```

You should see a device similar to **vg0-lv0** in the list.  If so, mount it by specifying the file-system type:

```

sudo mkdir /mnt/seagate_recovery
sudo mount -t ext3 /dev/mapper/vg0-lv0 /mnt/seagate_recovery

```

You should be able to access it now under **/mnt/seagate_recovery**...

That's all there was to it for me!

Good luck

---

