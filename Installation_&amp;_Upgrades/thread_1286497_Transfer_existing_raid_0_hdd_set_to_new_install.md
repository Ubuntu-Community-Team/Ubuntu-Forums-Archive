---
title: "Transfer existing raid 0 hdd set to new install"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by deepsiks on 2009-10-09
Currently I'm running Ubuntu Linux 8.10 on my server.  I have a 36gb hdd for the OS and two 1tb hdd's raid0 with linux mdadm for storage.  Can I throw my raid0 set into a newly built server running 9.04 and maintain the data and functionality on my raid set?

Thanks.

---

### Post by deepsiks on 2009-10-11
As it turns out, the newly built server detected the software raid set once I installed mdadm with apt-get.  It didn't mount it since it wasn't in fstab - no surprise there.  As a just-in-case I copied the old mdadm config file and old fstab for reference.  Only thing I had to tweak was the fstab for mounting the raid and now all is fine.

---

