---
title: "how to format usb pen drives?"
date: 2009-01-17
forum: Hardware
---

### Post by podapoda on 2009-01-17
How do i format my pen drives that i connect in ubuntu 8 like i do in windows?
i am a newbee to linux.
thanks in advance.

---

### Post by ugm6hr on 2009-01-17
Easiest way is to use Partition Editor:

```
sudo apt-get install gparted
```

System -> Administration -> Partition Editor

Select the device (often /dev/sdb), and then use common sense from there.

I would recommend formatting in "FAT32"

---

### Post by 00b00nt00 on 2009-01-17
If you live in fear of the command line, you can also do a search for gparted in synaptic package manager.

---

### Post by podapoda on 2009-01-19
thanks a lot:)

---

