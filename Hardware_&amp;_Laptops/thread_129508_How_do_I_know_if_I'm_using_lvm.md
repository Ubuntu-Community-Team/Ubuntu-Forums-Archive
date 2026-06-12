---
title: "How do I know if I'm using lvm"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by LordRaiden on 2006-02-13
I want to remove lvm from boot-time using sysv-rc-conf, but I don't know if I need it. I'd like to know how can I can figure (using console or otherwise) if I'm using lvm or not.

Thanks in advance

BTW:  I'm not using RAID

---

### Post by heimo on 2006-02-13
You would probably know if you set it up. It's not used by default. I don't know if this is correct way to test it, but you could run:
```
sudo lvmdiskscan
```
and see how many LVM volumes you have. (It'll also show your normal partitions.)  It should be safe to turn off lvm, but personally I don't see any need.

---

### Post by LordRaiden on 2006-02-13
Thank you

---

