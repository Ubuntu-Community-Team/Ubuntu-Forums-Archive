---
title: "No sound. Realtek drivers."
date: 2009-09-19
forum: Hardware
---

### Post by Xanza on 2009-09-19
First of, I'm really really new to linux.

So I installed ubuntu today and noticed there's no sound. I went to realtek's website to get the drivers but I don't know how to install them. Kindly help please. Remember I'm really new to this.

---

### Post by khelben1979 on 2009-09-19
Those drivers are hopefully in your Linux kernel.

With the alsaconf program (it's part of [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture")) you have the possibility to choose which sound device to use and with [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")gui you can check the volume meters to see that everything is set up high.

You also have the possibility to load the proper kernel module with either insmod or [modprobe]("http://en.wikipedia.org/wiki/Modprobe").

---

### Post by Xanza on 2009-09-19
how do i check my alsa conf?

---

### Post by khelben1979 on 2009-09-19
Just type: sudo alsaconf from a text console somewhere.

If the system don't find the command then it's not installed. There are other ways of doing this. I'm sorry I don't have Ubuntu installed over here (only Debian) so it get's a little difficult as usual, but you can start by exploring the menu system and look for something called: hardware drivers.

---

