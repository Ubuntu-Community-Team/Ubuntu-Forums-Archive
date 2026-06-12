---
title: "Compiling touchscreen support into M700 Tablet"
date: 2008-06-07
forum: Hardware
---

### Post by Mars Thrax on 2008-06-07
I recently purchased a Toshiba Protege M700 with touchscreen and tablet support. I followed the posted instructions for setting up the machine ([https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)), and currently have the stylus working. However, since I chose to use Ubuntu 64-bit, the "simple" method for enabling the touch screen does not work for me (the driver appears to crash on boot, and I have no stylus, let alone touchscreen). So, I decided to compile it myself following the "hard" instructions. Unfortunately, I'm having trouble compiling it.

My first problem was that I needed to install the libxi headers (not mentioned in the instructions...only calls for build-essential, tk, tk-dev, and patch)
```
sudo apt-get install libxi-dev
```

However, now I'm at a loss. I am receiving a compile error staying that there are undefined references to the following in libwacomcfg:
XListInputDevices
XSetDeviceMode
XGetDeviceControl
XOpenDevice
XFreeDeviceControl
XChangeDeviceControl

Just by the names, these seem like standard functions from the xi library, so I'm not quite sure why the compiler can't find them.

Any input would be greatly appreciated.

---

### Post by Mars Thrax on 2008-06-08
bump

---

### Post by prshah on 2008-06-10
> **Mars Thrax said:**
> 

```
sudo apt-get install libxi-dev
```




Just a suggestion; why not install libxi6 as well? As far as I understand, the -dev will contain only references to interfaces; the interfaces have to be defined with code which I assume will be in the libXi.so.6 library, which can be had from libxi6.

---

