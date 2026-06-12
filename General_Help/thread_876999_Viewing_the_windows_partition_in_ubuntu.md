---
title: "Viewing the windows partition in ubuntu"
date: 2008-08-01
forum: General Help
---

### Post by Downfall on 2008-08-01
Hello,

I partitioned my 500 GB in two to install Ubuntu.  I want to copy some files that are in my windows partition over to my ubuntu partition.  I could just shuttle them in a thumb drive, but it would be easier if I could just view the windows partition from inside ubuntu and copy what I want.  Is this possible?

Thanks.

---

### Post by Choad on 2008-08-01
this should be set up by default in gutsy... is there not an icon representing your windows partition in the places menu?

---

### Post by vanadium on 2008-08-01
This thread should better be moved to the Absolute Beginners section.

Indeed, since Hardy, Windows partitions are only mounted "on demand", this is when you try to access them via the Places menu.

Make sure Windows has been properly shut down (not hibernated) before accessing your Windows partition. If Windows is only hibernated, the partition is not "closed" and for safety, Ubuntu will not automatically open the partition: thus you will not have access to it.

---

### Post by Diabolis on 2008-08-01
If for some reason you don't have an icon to your windows partition in your desktop. Then you have to add it to your fstab file.

Open the file:
```
sudo gedti /etc/fstab
```

Then you have to add an entry for your drive. Is your windows partition a ntfs file system? (probably is)

---

### Post by Downfall on 2008-08-01
Hello,

It's there in system places.  I didn't know to look for it there.  As I should have noted, absolute beginner.  Thanks everybody, and sorry if I posted this in the wrong forum.

---

