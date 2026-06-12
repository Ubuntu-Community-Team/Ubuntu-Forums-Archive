---
title: "How to rid Removable Devices on Desktop"
date: 2008-08-23
forum: General Help
---

### Post by kwagster on 2008-08-23
The auto-appearing Removable Devices on the Desktop has annoyed me enough.
What is the easiest way to remove this feature?

Sorry if this was answered already.
I've spent a good 25 minutes (decent amount) searching around for it but haven't had any luck.
I'm hoping its a quick fix.
Thanks guys.

---

### Post by Rocket2DMn on 2008-08-23
Can you please post the output of these commands
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
If possible, can you tell us what drives are appearing that you don't want.  Thanks.

---

### Post by rbc on 2008-08-23
Alt+F2, then type in gconf-editor in the space. Then navigate apps-->nautilus-->desktop, then uncheck "Volumes visible"

---

### Post by kwagster on 2008-08-24
> **rbc said:**
> Alt+F2, then type in gconf-editor in the space. Then navigate apps-->nautilus-->desktop, then uncheck "Volumes visible"

Thanks that did the trick.

---

