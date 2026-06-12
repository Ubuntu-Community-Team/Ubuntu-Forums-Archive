---
title: "convert ntfs to ext from within Linux"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by salsaseb on 2005-12-05
Just finished installing ubuntu 5.10 on my laptop as single-boot system, totally formatting windows off the drive.
However, I realized I forgot to prep my external USB hard drive (80Gb - that contains music and documents) which has NTFS file system.
Would like to convert the fs to ext3, but can't use Win-based tools like Partition Magic to do so without losing the data (since I no longer have Win installed).
Is there a Linux-native equivalent to PM that will do the job?

---

### Post by SavageBeginner on 2005-12-05
You could try gparted, but I'm not sure if you can do this without loosing data.

---

### Post by manicka on 2005-12-05
An equivalent tool to pm in Linux is gparted but unfortunately it can't convert the drive without deleting the data

---

