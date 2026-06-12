---
title: "UBUNTU 9.04 Hangs after installing NVIDIA Drivers"
date: 2009-08-12
forum: Hardware
---

### Post by amol_nayak311 on 2009-08-12
I Have a dell Studio XPS With Nvidia 9500 M Graphics card.
I Installed the driver "NVIDIA Accelerated graphics driver (Version 180)" in it.

Now whenever i start eclipse and click on any of the buttons everything hangs, the keyboard nor the mouse works, CTRL + ALR + backspace doesnt work either.

However when i removed the NVIDIA driver it works fine.. Can some body help me out in this to identify the cause of this problem?

---

### Post by Deiu on 2009-08-12
I suggest installing the latest drivers from nvidia ftp server, not from the website (outdated?). Depending on your architecture, you can get the 32-bit version from [ftp://download.nvidia.com/XFree86/Linux-x86/190.18/](ftp://download.nvidia.com/XFree86/Linux-x86/190.18/), or the 64-bit from [ftp://download.nvidia.com/XFree86/Linux-x86_64/190.18/](ftp://download.nvidia.com/XFree86/Linux-x86_64/190.18/).

Good luck! 

P.S. In case you need a guide to do all that, check out this blog entry: [http://andrei.envisioningtech.net/2009/08/geforce-gt220-linux/](http://andrei.envisioningtech.net/2009/08/geforce-gt220-linux/). It covers the install for the GT220 model, but the principle is the same.

---

