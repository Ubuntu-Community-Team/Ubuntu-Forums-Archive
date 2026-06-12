---
title: "Does Nforce 430/410 integrated sound/NIC work?"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by olliraa on 2005-11-14
Hi,

building a Micro-atx computer that uses Asus A8N-VM CSM mobo. The board appears to ne great, but I was wondering if Ubuntu/kubuntu has problems with those Nforce 430/410 integrated features (sound, NIC) Any experiences?

---

### Post by kosmic on 2005-11-14
Hum I can only help about the Asus A8V-Deluxe and it all works ok
 
but have a look at the hardware suported by ubuntu - [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28nforce%29]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards?highlight=%28nforce%29")
 
 
look likes it works ok :)

---

### Post by gaspedalo on 2005-12-07
A little bit late, but maybe you still haven't decided yet. I got the graphics working with the new drivers from nvidia in a minute. They seem to be excellent. The NIC card driver has troubles because the forcedeth driver interferes and it's only being removed with a workaround. The worst case is sound. I managed to hear stuff, but either with a bad quality and a high frequency sound in the back... no foreground or with crashing after a minute playing (prior I had to patch the kernel..pooh). This all happened with the latest Alsa driver. Don't rely on the Asus distrubuted drivers, they are a joke. That's pure marketing and "letthecutsomerstryitout".

---

