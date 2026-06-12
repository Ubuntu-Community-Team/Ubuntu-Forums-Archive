---
title: "NTFS harddrive stuck at read only"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by shardrock on 2007-12-26
Hi,
I might be doing this a little backwards but it's worth a shot I guess.

I recently bought a Seagate FreeAgent Pro and was using it with Ubuntu without a problem. for some reason when I tried to back up my files on my Vista computer it turned the HDD to write only. I've changed the permissions multiple times with no actual change. i pretty much need it to be NTFS since I use it between two computers, so formatting it as a linux partition is out of the question ..i think..any ideas?

---

### Post by Yellow Pasque on 2007-12-26
Ubuntu 7.10 (Gutsy) should have NTFS read/write support IIRC. If you're using something earlier, I believe you need the ntfs-3g package. When the drive mounts, go to a terminal and type:
```
mount
``` to see if it's truly mounted as read-only, or if Ubuntu is just giving you a hard time since you don't have root access.

---

### Post by nick_h on 2007-12-26
It would be helpful if you posted the output of:
```
cat /etc/fstab
```

---

