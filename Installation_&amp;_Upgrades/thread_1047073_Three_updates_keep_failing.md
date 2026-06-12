---
title: "Three updates keep failing"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Yesideez on 2009-01-22
Every time I boot up I get "You have updates" but when I try and download them I get this:

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-21.43_i386.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.14-21.51_all.deb
  404 Not Found


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.14-21.51_i386.deb
  404 Not Found
```

Anyone know how I can get this sorted? Very new to Ubuntu still, running multi-boot.

---

### Post by Partyboi2 on 2009-01-22
Try changing your download server in Software Sources (System>Admin>Software Sources) 1st tab.

---

### Post by Yesideez on 2009-01-22
Thank-you very much!

Just changed from United Kingdom to "main" and it changed from 3 updates to 141...

:D

---

