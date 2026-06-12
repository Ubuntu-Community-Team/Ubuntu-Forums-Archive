---
title: "Disable x server"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by boris357 on 2007-04-28
I want to install the latest NVIDIA drivers for Ubuntu 7.04 Feisty Fawn but need to disable the x server to do it and then restart the x server. I have forgotten the commands from the terminal to do that. Could some one please post them. Thank you.

---

### Post by aysiu on 2007-04-28
Press Control-Alt-F1

Log in

Type ```
sudo /etc/init.d/gdm stop
```

Do all the commands to install the latest Nvidia drivers then finally ```
sudo /etc/init.d/gdm restart
```

---

