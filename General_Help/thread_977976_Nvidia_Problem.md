---
title: "Nvidia Problem"
date: 2008-11-10
forum: General Help
---

### Post by parliament on 2008-11-10
Hello, i just registered to forum and upgraded my old ubuntu to 8.10

First of all im sorry for my english.
My question is about the screen resolution on Ubuntu8.10.
I have Samsung 206BW monitor that have max resolution og 1650x1080.
In ubuntu theres 1600x1024 and 1600x1200 screen resolutions.
This is not a big problem but i just want to know how can i use the max resolution for my monitor.

Thanks
K.

---

### Post by parliament on 2008-12-01
Does anyone has an idea?

---

### Post by celem on 2008-12-01
The Nvidia drivers are proprietary and thus are not loaded by default. However, you click SYSTEM->Administration->Hardware Drivers and Ubuntu will present an option to load the Nvidia drivers. I use Nvidia's 177 driver with Ubuntu 8.10 and it will yield the full resolution of your monitor and will support the eye candy, if you want that stuff. Personally I turn it off.

I recommend that you make a copy of the xorg.conf file before and after the driver load and that you keep the copies handy in the root directory so that you can easily replace it with the restore boot's shell should you ever have a problem. For example:

Before you load the Nvidia driver:
sudo cp /etc/X11/xorg.conf /xorg.conf.original

After you load the Nvidia driver:
sudo cp /etc/X11/xorg.conf /xorg.conf.nvidia

---

