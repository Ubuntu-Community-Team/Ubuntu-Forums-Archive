---
title: "Raid Folder not writable"
date: 2010-02-02
forum: Hardware
---

### Post by AmbiguousOutlier on 2010-02-02
Hi, I've just set up my two 1tb hdd as a raid1. Mounted on /media/sdb1. I tried to create a folder on this mount however it said I didn't have permission. So I went to the terminal:

```

ls -l /media/sdb1

```
returns;

```

drw------ 2 root root 

```

then I did;

```

sudo chmod ugo+rwx /media/sdb1
ls -l /media/sdb1

```

as per 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

returned;

```

drw------ 2 root root 

```

Still no permission to write to that folder, have I done something wrong?

---

