---
title: "Deny Access to NTFS Partition"
date: 2008-08-12
forum: General Help
---

### Post by marcosconio on 2008-08-12
Hi!

Anybody knows if that is posible?

I tried some suggestions from other threads, like [http://ubuntuforums.org/showthread.php?t=884853&highlight=ntfs+partition+hardy]("http://ubuntuforums.org/showthread.php?t=884853&highlight=ntfs+partition+hardy"), and I can't have a solution.

My /etc/fstab line is:
```
UUID=5E14EC7214EC4E99 /media/windows  ntfs-3g    auto,owner,uid=1000,gid=0,utf8,dmask=027,fmask=137 0       1
```
and if I login with other user than marcos, I can access to the partition with no problems.

I'm in Hardy.

And... Sorry for my english!!

Thanks,
Marcos Alcazar
Mendoza, Argentina

---

