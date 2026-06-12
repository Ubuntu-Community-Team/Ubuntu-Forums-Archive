---
title: "nvidia  GeForce 7200"
date: 2009-07-13
forum: Hardware
---

### Post by avidesh on 2009-07-13
Hello,
I installed Nvidia GeForce 7200 card to my desktop. and now the X does not start.I was using the onboard graphics before.
Please suggest

---

### Post by master_kernel on 2009-07-13
You need to install the driver for it. To get to your desktop, boot into recovery mode, and enter:
```
dpkg-reconfigure -phigh xserver-xorg
```

Then continue booting (ctrl-D) and follow the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

