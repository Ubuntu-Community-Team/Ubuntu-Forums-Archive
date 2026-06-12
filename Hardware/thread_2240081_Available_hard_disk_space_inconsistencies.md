---
title: "Available hard disk space inconsistencies"
date: 2014-08-17
forum: Hardware
---

### Post by Ratscallion on 2014-08-17
I have a 500GB external hard drive with a ~300GB ext3 partition.
On GParted, this partition has 269.6GB used, with 14.99GB remaining (total: 284.59GB)
In nautilus (and other file managers), the same partition has 300GB used, 816.3MB free (total 300.8GB). However, when looking at the drive in nautilus, "Contents: 32,530 items totalling 280GB".

How do I know which one is right, since obviously with nautilus I can't add a 1GB file to the drive without filling it up. If they're both right in some strange way, is there a way I can fix the inconsistency? 

Thanks.

---

### Post by bizhat on 2014-08-18
Go to the driver in terminal, run

```

du -h --max-depth=1

```

Also

```

df -h

```

Can give some information when partition is mounted.

---

### Post by Ratscallion on 2014-08-18
Thanks. Output of df -h is confusing me a little:
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       281G  266G  779M 100% /media/Misc
Taking used from size >> Available.
The first command with sudo aligns with the 'Used' amount too.

---

### Post by Elfy on 2014-08-18
Bear in mind that there will be, unless you've changed that, 5% reserved on that partition for root. 

[https://help.ubuntu.com/community/RecoverLostDiskSpace#Gain_Just_a_Bit_of_Space](https://help.ubuntu.com/community/RecoverLostDiskSpace#Gain_Just_a_Bit_of_Space) look at the tune2fs section

---

### Post by Ratscallion on 2014-08-18
> **Elfy said:**
> Bear in mind that there will be, unless you've changed that, 5% reserved on that partition for root. 

[https://help.ubuntu.com/community/RecoverLostDiskSpace#Gain_Just_a_Bit_of_Space](https://help.ubuntu.com/community/RecoverLostDiskSpace#Gain_Just_a_Bit_of_Space) look at the tune2fs section

Super, that's sorted it. Thanks very much! I don't think there was anything for the system there, since I only use it for media storage (rather than the OS). Hopefully it'll be fine :P

---

