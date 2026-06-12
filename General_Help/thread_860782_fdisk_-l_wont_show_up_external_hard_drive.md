---
title: "fdisk -l wont show up external hard drive"
date: 2008-07-15
forum: General Help
---

### Post by ilovelinux33467 on 2008-07-15
I have a 500 GB Western Digital External Hard Drive connected to a VMware Server Virtual Machine (I have checked in vmware removable devices and it says its mounted) On a Ubuntu host. When i do sudo fdisk -l on the Server Virtual Machine it doesn't show up. Help anyone?

---

### Post by ilovelinux33467 on 2008-07-15
Help Please???

---

### Post by p_quarles on 2008-07-15
Try:
```
mount
```

---

### Post by ilovelinux33467 on 2008-07-15
doing mount didn't show it

---

### Post by p_quarles on 2008-07-15
So, can you explain more precisely what it is that *does* say it's mounted? I wasn't clear on that.

---

