---
title: "External HDD inaccessable"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by Jungle-Cat on 2007-06-12
My external drive "External320" is a single 320 gig NTFS partition (i have ntfs-config for all the patching etc).

However, when i try and access it at /media/External320/ its empty. Nothing in it at all. It was working perfectly fine last week. I can still access it OK under windows.

Anyone know how to fix this?

Cheers

---

### Post by taurus on 2007-06-12
How did you mount it?  Post

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Jungle-Cat on 2007-06-13
I didnt have to do any terminal things or mounting, Ubuntu automatically made an icon on the desktop (or Computer etc) and it was all accessible.

Please explain how to mount it. What you've posted above is useless to a noob like me.

---

