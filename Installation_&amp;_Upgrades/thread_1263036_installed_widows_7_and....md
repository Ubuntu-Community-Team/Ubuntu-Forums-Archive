---
title: "installed widows 7 and..."
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by BackwardsDown on 2009-09-10
**I have solved this problem myself, scroll down for the solution**

After installing windows 7 grub is gone. (doh). So I loaded up my recovery cd.

But I had like 10 partitions. (Ubuntu was on sda8). But ls /dev/ only gives me /dev/sda, /dev/sda1 (Windows 7), /dev/sda2, /dev/sda10 atm!

Anyone that can help me with this? I hope I can recover my data :)



**Before installing:**
```
sda1: 100GB
sda2: 400GB
   sda3: 30GB
   sda4: 20GB
   sda5: 30GB
   sda6: 20GB
   sda7: 30GB
   sda8: 20GB (ubuntu)
   sda9: 248 (home)
   sda10: 2GB (swap)
```

**After installing:**
```
sda1: 100GB
sda2: 400GB
   389 GB unacollated space (these were all my partitions and data!)
   sda10: 2GB (swap)
```


Is there any chance I can get my data back? Seems odd that windows didnt touch my swap parition...

**Solution**
If you have partitions that are suddently unaccolated, you'll **LOVE**  the program testdisk!

---

