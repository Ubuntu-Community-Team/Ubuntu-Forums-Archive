---
title: "Need help fixing video driver from recovery mode"
date: 2010-08-23
forum: Hardware
---

### Post by malkierie504 on 2010-08-23
I think i killed my video driver trying to fix the issue that people have been having with the ati x1200 mobile driver. I think in marking all of the old drivers for removal i didn't mark a new driver for installation. Now when i boot into the os i get a blank screen after grub if I don't go into recovery mode. if I type Xorg from the recovery terminal i get the same result, a black screen but i have sounds so i know something is there.

---

### Post by IcarusR on 2010-08-24
From terminal run...

```
sudo dpkg-reconfigure xserver-xorg
```

---

