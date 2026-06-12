---
title: "incorrect folder and true hard drive size?"
date: 2008-09-30
forum: Hardware
---

### Post by jmate24 on 2008-09-30
I have found that my SATA I hard drive is reporting the wrong folder size i have it mounted to my Videos folder and when I right click on the folder and select properties it reports that (see attached picture) there is more space used Than when I view it in Gparted (see next attached picture) and my df:
```
justin@justin-desktop:~$ df /dev/sdb1
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            969063944    204556 920021388   1% /home/justin/Videos
justin@justin-desktop:~$ 

```

What's wrong with this picture?

---

### Post by cariboo on 2008-09-30
Try:

```
df -h
```

To get a listing of your hard drive usage in a human readable form.

You should never rely on gui tools as most of the time they are wrong.

Jim

---

### Post by jpkotta on 2008-09-30
df and nautilus agree.  Remember that 1 GB = 1024 MB = 1048576 KB.  Don't know about gparted though.  It's probably measuring something different than df.  df only operates at the filesystem level, so it is probably missing the metadata used up by the filesystem.  gparted is probably measuring the raw space on the partition.
```
 920021388/2^20 = 877.400768280029
```
```
[969063944-920021388]/2^20 = 46.7706260681152
```

---

### Post by jmate24 on 2008-09-30
File system            Size  Used Avail Use% Mounted on
/dev/sdb1             925G  3.5G  875G   1% /home/justin/Videos

Well, I am going to try filling the drive completely full to see if it gives an error when i reach it's limit. It's going to take a while.

---

