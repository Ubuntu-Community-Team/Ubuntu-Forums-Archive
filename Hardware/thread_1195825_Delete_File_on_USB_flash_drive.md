---
title: "Delete File on USB flash drive"
date: 2009-06-24
forum: Hardware
---

### Post by jhouse59 on 2009-06-24
I've got two USB flash drives that is the same. One of them will not let me delete files on it and the other one will. The one that won't let me delete or write anything to it. I have to boot into Windows to copy to it. The last time I booted into Windows to copy and delete files on it. Every time I would open the drive it would crash. I done this about three times. How can I change this? And, why would it do this?

---

### Post by ddrichardson on 2009-06-24
I take it English is a second language? Plug both in.

Need the output of:```
sudo fdisk -l
mount
```Will also need the permissions, replace PATH with the path to the device:```
ls -l /media/PATH
```

---

### Post by jhouse59 on 2009-06-24
> **ddrichardson said:**
> I take it English is a second language?
No,it's the only one I know. I'm still trying to learn it.:)
I tried  the commands and still no luck.


> Will also need the permissions...
How can I get permission for this device.

---

### Post by ddrichardson on 2009-06-24
Dude, I need the OUTPUT from those commands for diagnostics they weren't going to fix it. Open a terminal and type them in, then copy and paste the output in here!

---

