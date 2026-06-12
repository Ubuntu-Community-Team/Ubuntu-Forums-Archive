---
title: "Nvidia 9500 GT drivers issue."
date: 2009-08-10
forum: Hardware
---

### Post by Mysidic on 2009-08-10
Hello, I recently got an nvidia 9500 GT graphics card, and installed the acclerated graphics drivers via "Hardware Drivers" control panel and rebooted. However, while the "Hardware driver" indicates it is installed, I cannot run blender, google earth, or desktop effects, and I think the graphics drivers are wrong. Do I need to do something else, or could the problem be something else? 

I'm running ubuntu 9.04 on a 64bit dual core athalon with 2GB of RAM.

---

### Post by dagrump on 2009-08-10
Open the terminal & type sudo nvidia-xconfig that will write a new xorg.conf file, then reboot. 
Installing the drivers only adds a driver line which really isn't much good.

---

### Post by Mysidic on 2009-08-11
Tried that, but it seems to have done nothing. Anything else I may be missing?

---

### Post by hdixon on 2009-09-09
> **Mysidic said:**
> Tried that, but it seems to have done nothing. Anything else I may be missing?


Did you ever get this card working properly? I was looking at maybe using the same card.

---

