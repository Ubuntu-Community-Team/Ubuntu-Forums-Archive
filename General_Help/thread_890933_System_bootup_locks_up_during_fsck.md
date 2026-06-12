---
title: "System bootup locks up during fsck"
date: 2008-08-15
forum: General Help
---

### Post by matmcnic on 2008-08-15
Ubuntu 8.0.4.1 running inside VMWare Server.

When I boot the system it locks up (the console shows it is on fsck /dev/sda1....)

I did the recovery bootup and selected Repair Broken Packages and that curred it... but I was wondering if anyone has seen this behavior or has ideas on why it happened?

Thank you!

---

### Post by bodhi.zazen on 2008-08-15
Try booting your VM with a .iso and running fsck on /dev/sda1 from there ...

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

        if that fails

```
fsck -fvy /dev/sda1
```

---

