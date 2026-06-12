---
title: "Missing hard drives, &quot;can't handle computer:locations&quot;"
date: 2008-09-21
forum: General Help
---

### Post by PostersandGuitar on 2008-09-21
Ubuntu is suddenly not displaying my hard drive, or giving me the option to mount it. when I try to go to computer, it says "Nautilus can't handle computer:locations"

On the advice of Google I attempted:

sudo apt-get install --reinstall nautilus
sudo dpkg --configure -a
and
sudo apt-get install -f

with no effect.

Help?

---

### Post by PostersandGuitar on 2008-09-21
If any information is needed, please tell me.

---

### Post by cariboo on 2008-09-21
Could you paste the output of:

```
sudo fdisk -l
```

and paste into you next post. Even though nautilus is broken you should still be able to mount your disks manually, until you get things fixed.

Jim

---

