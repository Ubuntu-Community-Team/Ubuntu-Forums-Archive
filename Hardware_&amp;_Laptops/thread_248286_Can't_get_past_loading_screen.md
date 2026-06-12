---
title: "Can't get past loading screen"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by Cojawfee on 2006-08-31
I successfully installed Ubuntu. When booting up I select Ubuntu from the grub and it starts up. It shows all the things loading, configuring drivers, all that stuff. It finishes, shows the cursor, it flashes for a bit, then hangs.

I can access the command line by pressing Ctrl + Alt + F1. I checked another thread and someone said something about nVidia drivers and supplied the following:

```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```

I typed in the two things and everything seemed to work OK. I restarted (I couldn't figure out how to do it any other way, so I just pressed the reset button). I boot up Ubuntu, it displays the cursor, and then hangs again.

I've also heard that Ubuntu doesn't like nForce 5 chipsets. Though through searching I haven't found any solutions other than the one thing I tried. Mainly just that people are also having problems.

Any help would be appreciated. I really liked using the LiveCD on my old computer, and would really like to use Ubuntu on my new computer (where I have a spare hard drive).

Specs:

ASUS M2NSLI Deluxe (socket AM2, nForce 570 chipset)
AMD Athlon 64 X2 4200
Two GeForce 7600's

---

