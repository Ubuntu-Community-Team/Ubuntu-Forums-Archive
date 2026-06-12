---
title: "nvidia drivers for Feisty Fawn?"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by drev on 2007-03-05
Hey everybody.  I got a hold of Feisty Fawn, and am about to install it on my laptop (HP Pavilion dv9000, nVidia GeForce Go 6150, 1GB RAM, 64-bit, etc.)  I've been having trouble getting the drivers for the graphics card installed on 6.06 and 6.10.  I decided to go with Feisty since I need the headphone jack to work (it didn't in 6.06 nor 6.10).  I'd really like to stick with this version, so can anyone guide me through installing the drivers for the GeForce Go 6150 graphics card?  Is it any different than the 6.x versions?

So far, the graphics card is the only thing I've consistently had problems with.


Thanks in advance

---

### Post by andreas64 on 2007-03-05
Hi,

enable the multiverse repos and install the driver through synaptic. I've got no problems with this (GeForce Go 7600)

Andreas

---

### Post by drev on 2007-03-06
I don't see any "multiverse" repositories.  I've tried installing (via Synaptic) nvidia-glx, and any other 'nvidia' thing I could think of.  I tried installing all of the repositories for all versions of the kernel I have... still nothing.

On a related note... when I attempt to install Feisty Fawn, it says that it's possible Feisty might resize partitions and that I should backup data, etc.  Do I need to worry about Feisty wiping my Windows partition?  Or is that just a general warning that I can (more or less) blow off?

Thanks

---

### Post by teh.element on 2007-04-30
Actually if you are installing the drivers in Fiesty all you need to do is to use the Restricted Drivers Manager to d/l and install the driver for you, OR you can do it how i did and install it using Automatix2. The driver from Automatix2 has almost the exact same settings as the NVIDIA driver has for WinXP. Its really sweet. Take that ATI!

---

