---
title: "FSCK Error w/ external ext2 usb hard drive"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by Stoffer on 2008-02-25
My external hard drive somehow got corrupted, and I ran fsck a few times on it.  It keeps exiting with this error:

```
Pass 3: Checking directory connectivity
Unconnected directory inode 49153 (...)
Connect to /lost+found<y>? yes

Unconnected directory inode 68211 (/???)
Connect to /lost+found<y>? yes

Unconnected directory inode 6406145 (...)
Connect to /lost+found<y>? yes

Pass 3A: Optimizing directories
Warning... fsck.ext2 for device /dev/sda1 exited with signal 11.
krzysztof@Stoffbox:~$    
```

What does that mean?

---

