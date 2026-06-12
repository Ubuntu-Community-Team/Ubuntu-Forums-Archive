---
title: "3TB WD My Book Live NAS NIC controller took dump."
date: 2013-12-28
forum: Hardware
---

### Post by d1ringer on 2013-12-28
The controller board on my WD My Book Live NAS 3 TB took a dump. Tried to access with SATA hook up to mobo in win 7 and shows Linux partitions. I've tried to access in Xubuntu but can't see it. Any help for this NOOB would be appreciated! :confused:

---

### Post by oldfred on 2013-12-29
Windows will not correctly see Linux partitions, so that does not tell anything about the drive or partitions.

Better to use Ubuntu live installer of same version as your install and check from that.

---

### Post by d1ringer on 2013-12-30
That's the problem with the Western Digital NAS MyBookLive. The Nic took a dump and the drive wouldn't access anymore. I removed the drive from the enclosure to try to retrieve the data. I used DiskIntenals to see the partitions but through Windows it just says Linux partitions. How would I find out the Linux version of the NAS drive?

---

### Post by oldfred on 2013-12-30
So this is not a Linux install, just your MyBookLive? Those may use unusual formats or encrypt data for your "protection". 

If Linux formats you should see the format type with this.
sudo parted -l
Or download gdisk as it may be gpt partitioned. If not gpt then they did something unusual with MBR and non-standard sector sizes which may be another issue.
sudo apt-get install gdisk
       sudo gdisk -l /dev/sdX # where X is your drive a, b or c?

---

### Post by d1ringer on 2013-12-31
Thanks! I'll try that. Happy New Year!

---

