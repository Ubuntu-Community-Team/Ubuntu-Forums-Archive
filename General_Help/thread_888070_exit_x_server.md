---
title: "exit x server"
date: 2008-08-12
forum: General Help
---

### Post by stkblazer on 2008-08-12
how do i exit an x server cause when i go to install my nvidia driver it says im running an x server and tells me to exit but id dont know how

---

### Post by DeathOnJuice on 2008-08-12
Press Ctrl-Alt-F1. This will take you to a terminal. Log in, then type sudo /etc/init.d/gdm stop. I think that should do it. Ctrl-Alt-F7 will take you back once you restart X.

---

### Post by WRDN on 2008-08-12
```
sudo /etc/init.d/gdm stop
```

This will stop the GNOME Display Manager

---

### Post by x1a4 on 2008-08-12
> **WRDN said:**
> This will stop the GNOME Display Manager
Correct.  The display manager will be stopped and all the displays (X servers) it's managing will be stopped with it.

stkblazer: why are you installing the driver from the Nvidia site?  You can install it from the repositories using the package manager.  Just install the **nvidia-glx-new** package.

---

