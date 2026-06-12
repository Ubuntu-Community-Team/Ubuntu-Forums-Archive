---
title: "Installing Intel Drivers for Acer Aspire One Happy"
date: 2013-01-28
forum: Hardware
---

### Post by Light Glint on 2013-01-28
Hello

I have a Acer Aspire Happy, and i'm trying to see about the graphics drivers

This netbook contains a Intel GMA 3150, and I'm having a lot of trouble finding and installing drivers for it, or seeing if it already has done so.

Everything else on the system has worked brilliantly, except for a small issue when the thermal pad stopped responding once.

I intend to use this system for flash games, GBA emulators and Dosbox.

Thanks in advance.

---

### Post by Yellow Pasque on 2013-01-28
The intel drivers are open-source and loaded by default. Unless you're experiencing issues, it's probably best not to install any other drivers...

You can check the driver with glxinfo:
```
sudo apt-get install mesa-utils
glxinfo
```

---

