---
title: "Ubuntu 8.04 Server /dev"
date: 2008-07-19
forum: General Help
---

### Post by philo23 on 2008-07-19
yesterday i installed a new hard drive inside my ubuntu server running 8.04 and was i was planning on mounting to a certain location this was all well and good until i realised theres no /dev/hda, /dev/hdb, /dev/sda or /dev/sdb so i dont see how i can mount anything.
any ideas anyone? i dont know how to or where to find the UUID of the drive and i'm unsure of the label.
if you could give me the command line version of this command as i connect to the server via ssh and its also head-less with no GUI running.  so some commands to reveal the uuid or show me where everythings moved to would be great. thanks.

---

### Post by RealPSL on 2008-07-19
Can you get output from ```
sudo fdisk -l
```

The following will list the uu-id of each disk and the corresponding partitions

```
ls -l /dev/disk/by-uuid
```

You can get labels with ```
ls -l /dev/disk/by-label
```

I would start with the uuid.

---

