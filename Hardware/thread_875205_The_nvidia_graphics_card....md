---
title: "The nvidia graphics card..."
date: 2008-07-30
forum: Hardware
---

### Post by Animeniac on 2008-07-30
I have downloaded the driver file from the Nvidia website. I have followed the directions on the page, until step 3. Step 3 says "type sh NVIDIA-Linux-x86-96.43.07-pkg1.run to install the driver". Whaaa???? I don't understand exactly what it means.

I typed it in Terminal, but it couldn't open the file. I typed it after I typed 'su', but I got the same error. I allowed execution on the file and then opened it and clicked 'Run', but nothing happened. I opened it again and clicked 'Run in Terminal', and then I got the error "must be run as root". I opened it by typing 'gksudo nautilus' in Terminal and then go to the file in the 'root' window, ran it in Terminal, but then got the error "X server is running".

What *else* do I have to do to install the graphics card driver? Exactly *where* do I have to type 'sh NVIDIA-Linux-x86-96.43.07-pkg1.run'?

I installed Ubuntu using Wubi, one time, and installed the "Nvidia accelerated graphics driver" from 'Hardware Drivers' in 'System', and it resulted in a low resolution. The reason why I want to install the driver downloaded form the Nvidia website is because I don't want to have a low **maximum** resolution, anymore.

By the way, the website is [http://www.nvidia.com/object/linux_display_x86_96.43.07.html](http://www.nvidia.com/object/linux_display_x86_96.43.07.html)

---

### Post by -random on 2008-07-30
what graphics card are you using?

(eg 8600, 9800, .. ) ?

try searching the forums for:

nvidia driver 8500

(or whatever card you use)

---

### Post by Animeniac on 2008-07-30
My graphics card is Geforce 4 MX 4000.

---

### Post by Animeniac on 2008-07-30
Never mind. I downloaded and installed EnvyNG and used it to automatically download the drivers for my Nvidia graphics card. When the computer restarted, it came out with a low resolution, but I am able to set it to a higher resolution in the 'NVIDIA X Server Settings' in 'System', so I did.

---

### Post by steveneddy on 2008-07-30
> **Animeniac said:**
> Never mind. I downloaded and installed EnvyNG and used it to automatically download the drivers for my Nvidia graphics card. When the computer restarted, it came out with a low resolution, but I am able to set it to a higher resolution in the 'NVIDIA X Server Settings' in 'System', so I did.

Could we mark this as solved then?

---

