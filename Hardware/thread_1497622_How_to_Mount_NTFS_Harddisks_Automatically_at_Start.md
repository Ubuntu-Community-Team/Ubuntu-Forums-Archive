---
title: "How to Mount NTFS Harddisks Automatically at Startup?"
date: 2010-05-30
forum: Hardware
---

### Post by guzelmarmara on 2010-05-30
I have two NTFS formatted SATA harddisks and I want to make them automatically mount at the startup. When I clicked Places-HDD1 they are mounting, but my startup programs must use these drives at the startup. How I can do this?

Thanks for your aprreciation...

---

### Post by drs305 on 2010-05-30
You can add entries to /etc/fstab, which will mount the drives before your user startup scripts are run.

The easiest way to add the entries is to install and use "ntfs-config".

Install it with 
```
sudo apt-get install ntfs-config ntfsprogs
```

Run it via System, Adminsitration, NTFS Configuration Tool.

You provide the information (partition and mountpoint) and it will automatically make an entry in fstab for NTFS partitions.

---

