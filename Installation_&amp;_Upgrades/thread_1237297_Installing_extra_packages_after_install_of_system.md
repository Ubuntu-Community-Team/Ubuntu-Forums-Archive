---
title: "Installing extra packages after install of system"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by Frezno71087 on 2009-08-11
Hi i just installed Ubuntu Studio. when i installed it i didn't know to press space to select the extra packages so i did not install any of the packages. I would like to install all of the packages and would like to do this without having to reinstall the whole system again. If this is possible that would be most champion. thanks ahead of time.

---

### Post by madhavhmk on 2009-08-11
I don't know abt this ubuntu studio thing...but ubuntu has synaptic manager....you can select any packages you want in it. it will download from the server and install them for you...

---

### Post by Partyboi2 on 2009-08-11
> **Frezno71087 said:**
> Hi i just installed Ubuntu Studio. when i installed it i didn't know to press space to select the extra packages so i did not install any of the packages. I would like to install all of the packages and would like to do this without having to reinstall the whole system again. If this is possible that would be most champion. thanks ahead of time.

Hi, you should be able to open a terminal (Applications>Accessories>Terminal) and install the packages with
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
``` seems like some people have had problems with the linux-rt package so you might not want to install that package.

---

