---
title: "Trying to enable restricted drivers"
date: 2008-07-18
forum: Hardware
---

### Post by cronk on 2008-07-18
Just reinstalled ubuntu 8.04 tonight and after getting started I wanted to enable restricted drivers for my nvidia graphics card.  I went through the normal process of simply clicking "enable" but immediately after it starts to try and download the driver I get this error:

```

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb
  404 Not Found

```

This seems like an issue with my network but I've got both a good wired connection and wireless.

---

### Post by Zack McCool on 2008-07-18
Try doing an update first...

```
 sudo apt-get update 
```

As the file that your system is looking for isn't there.  The update should give the latest file list...

---

### Post by cronk on 2008-07-18
After a few updates and a restart it finally installed it. Took a good 30 mins to get it working which os funny, never had a problem with it before.

Thanks for the help.

---

### Post by hansdown on 2008-07-18
Glad zack mcCool's advice helped cronk.

---

