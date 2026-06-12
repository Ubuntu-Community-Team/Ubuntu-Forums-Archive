---
title: "Growing RAID 1 Partition"
date: 2008-10-14
forum: General Help
---

### Post by igb on 2008-10-14
One of the RAID 1 disks on my Myth box has died. Rather than simply replace it with one of the same size I am going to get two larger drives. The current partitioning is like:

/dev/md0 / (root partition)
/dev/md1 swap
/dev/md2 /home (contains recordings)

I don't plan on increasing the size of md0 or md1, but want to increase md2 to use the full capacity of the new drive.

What I thought of doing was install new bigger disk. Create three partitions the same size as on the existing drive. Use mdadm --add to add these new partitions to the arrays. Wait until everything has synced.

Remove old smaller drive and add the other new larger drive. create three partitions and add these back to the raid arrays. Wait until everything is synced.

Now it seems that I can use mdadm --grow /dev/md2 --size=max to increase the size of /dev/md2 to fill the whole disk.

From my research this resizes the RAID, but not the file system. So after it has finished I must run resize2fs /dev/md2. Is this correct? Is there an easier way of achieving what I want?

Ian.

---

