---
title: "[SOLVED] update ubuntu server kernel"
date: 2008-10-18
forum: General Help
---

### Post by Woody1987 on 2008-10-18
Im trying to update my ubuntu server 8.04 box to a newer kernel that has become available but it wont let me. It says:

```
The following packages have been kept back:
  linux-headers-generic linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Why is this?

---

### Post by Nepherte on 2008-10-18
Try
```
sudo apt-get dist-upgrade
```

---

### Post by Woody1987 on 2008-10-18
Thanks that worked

---

