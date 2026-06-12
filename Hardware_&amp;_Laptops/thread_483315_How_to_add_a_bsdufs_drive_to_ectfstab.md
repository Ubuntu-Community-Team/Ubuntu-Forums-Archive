---
title: "How to add a bsd/ufs drive to /ect/fstab"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by elev on 2007-06-24
Using this site:
[http://faqs.pcbsd.org/9_292_en.html](http://faqs.pcbsd.org/9_292_en.html)
I was able to mount the drive with this command:
```
sudo mount -r -t ufs -o ufstype=ufs2 /dev/hdb1 /media/shared_media
```

Please, please, please help me translate the above command into an fstab line.
So far I tried this: 
```
/dev/hdb1     /media/shared_media ufs auto , ro, ufstype=ufs2, nodev, nosuid,    0   0
```

when I ```
sudo mount -a
``` after that I get > [mntent]: line 12 in /ect/fstab is bad

help!!!!

---

### Post by Bachstelze on 2007-06-24
Just remove the spaces after the commas :

```
/dev/hdb1     /media/shared_media ufs auto,ro,ufstype=ufs2,nodev,nosuid    0   0
```

---

### Post by elev on 2007-06-24
Ahhh!  Woohoo! Thank you so much!

---

