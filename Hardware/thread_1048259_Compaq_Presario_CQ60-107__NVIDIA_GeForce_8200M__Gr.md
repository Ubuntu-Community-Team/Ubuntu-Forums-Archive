---
title: "Compaq Presario CQ60-107 | NVIDIA GeForce 8200M | Graphics Problem"
date: 2009-01-23
forum: Hardware
---

### Post by reeksy on 2009-01-23
Hi Guys.

I've got a new laptop. Here's the basic spec:

**Compaq Presario CQ60-107 15.6-inch Laptop, AMD Sempron, 1GB RAM, 120GB HDD, NVIDIA GeForce 8200M**

I've just installed the latest version of Ubuntu (GNOME) but it has really choppy graphics behaviour for some reason. 

For example; when I drag a window around the screen it takes an age to render it. It jumps from position to position drawing it (from top to bottom). It's like if you have an install of Windows and it hasn't picked up your graphics card; everything is really slow to respond/render.

My guess is that Ubuntu hasn't picked up my graphics card at all. 

Does anyone know how I combat this?

Thanks,
Reeksy.

---

### Post by patchoro on 2009-02-19
[I]You'll need to install the restricted drivers.
On my CQ60 notebook with the 8200M and Ubuntu Intrepid I use driver version 177.82 which makes a big difference. You get snappy window management and 3d performs quite well.
 
The drivers are not all they should be because flash video performance remains dramatic! Hopefully this will be resolved in the future.

ps: using the 173 driver got me a much improved flash video performance. So I can recommend that one.[/I]

**pps: forget all posts above. Just go for the 180 drivers and all will be well!**

---

### Post by bibimidi on 2009-04-06
Hey reeksy musta na?

Were you able to fix your nvidia driver problem? I have the same machine spec as yours and having the same problem. I have gone a lot installing/reinstalling various versions but now and then my screen hangs up. I have to switch to virtual terminal and back just to do a quick fix.

If you got it working kindly let me see your xorg.conf and your driver version. Presently i have the 180.44 version preinstalled. I know the 185.13 beta is out in fact i tried it in 8.10 but same problem. Strange thing this beta i got working in Jaunty alpha. When i reverted to 8.10 the problem started to show up. I experience this in Mint 6 as well and until now im looking for a solution.

Please let me know what u have ok? Peace :p

Regards,
bibs



> **reeksy said:**
> Hi Guys.

I've got a new laptop. Here's the basic spec:

**Compaq Presario CQ60-107 15.6-inch Laptop, AMD Sempron, 1GB RAM, 120GB HDD, NVIDIA GeForce 8200M**

I've just installed the latest version of Ubuntu (GNOME) but it has really choppy graphics behaviour for some reason. 

For example; when I drag a window around the screen it takes an age to render it. It jumps from position to position drawing it (from top to bottom). It's like if you have an install of Windows and it hasn't picked up your graphics card; everything is really slow to respond/render.

My guess is that Ubuntu hasn't picked up my graphics card at all. 

Does anyone know how I combat this?

Thanks,
Reeksy.

---

