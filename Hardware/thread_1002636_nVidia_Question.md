---
title: "nVidia Question"
date: 2008-12-05
forum: Hardware
---

### Post by almigi on 2008-12-05
My computer's graphics card (well, integrated graphics chip) is a Nvidia GeForce 6150 SE, and I have a couple of questions about installing the driver.

Does it matter how I install the driver? Is there really any difference in between using System > Administration > Hardware Drivers or using Envy?

Also, I've heard that there's some problems with 3d acceleration using the 177 and 173 series drivers.  If I'm planning on doing anything graphics intense, should I install the 96 series driver until a new one comes out (I hear that nVidia is beta testing a new one right now).

If it helps, here's some more status about my Computer: AMD Athlon X2 4800 Dual-Core Processor, 3GB of RAM, and I'm using the amd64 version of 8.10.

Thanks.

- Al

---

### Post by kpkeerthi on 2008-12-05
If you are not sure what to do, install using Hardware Drivers. This route gets you the driver from ubuntu official repository.

If you use envy, you are most likely to get the latest nvidia driver off NVIDIA website.

---

### Post by vgrisham on 2008-12-05
I highly recommend installing the beta driver that is now out. I installed it two weeks ago, and it has been stable, and it has resolved the weird problems that I was having with my window borders being mis-drawn as well as white line issues with Avant-Window-Navigator. 

The driver was very easy to install. Just download the driver from [here]("http://www.nvidia.com/object/linux_display_amd64_180.06.html") and logout. Ctrl-Alt-F4 into your tty terminal and shut down the x server (code: sudo /etc/init.d/gdm stop). Then navigate to the directory where you saved the driver and code "sudo sh (name of file).run" I answered yes to every question and didn't run into any difficulties.

---

### Post by vgrisham on 2008-12-07
How did it go? Did you get the beta driver going?

---

### Post by loomsen on 2008-12-07
> **vgrisham said:**
> I highly recommend installing the beta driver that is now out. I installed it two weeks ago, and it has been stable, and it has resolved the weird problems that I was having with my window borders being mis-drawn as well as white line issues with Avant-Window-Navigator. 

The driver was very easy to install. Just download the driver from [here]("http://www.nvidia.com/object/linux_display_amd64_180.06.html") and logout. Ctrl-Alt-F4 into your tty terminal and shut down the x server (code: sudo /etc/init.d/gdm stop). Then navigate to the directory where you saved the driver and code "sudo sh (name of file).run" I answered yes to every question and didn't run into any difficulties.

#2

Plus take a look at the thread in my sig on fixing permissions for accessing your devices direct rendering and 3D enhancement functions.

---

