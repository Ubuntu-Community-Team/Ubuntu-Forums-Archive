---
title: "Can I use ndiswrapper for installing USB drivers?"
date: 2012-06-11
forum: Hardware
---

### Post by Los Frijoles on 2012-06-11
I have a desktop which has an ASRock Z68 Pro3-M motherboard. I recently bought a really nice flash drive which on Windows can be read/written at 30-50MB/s. I think this is in part due to this 'XFastUSB' hardware stuff that the motherboard has. I then got to wondering if I could install the specific driver for the USB ports on Ubuntu using ndiswrapper. I don't want to break anything and I have only used ndiswrapper for wireless drivers, so does anyone know to what extent I can use ndiswrapper for installing windows drivers?

---

### Post by Cheesemill on 2012-06-11
ndiswrapper only works for network drivers, it won't work for anything else.

---

### Post by Yellow Pasque on 2012-06-11
The USB 3.0 ports are powered by an Etron EJ168A chipset. I see other people complaining that this chipset isn't supported by Linux, but the most recent comments I can find are about a year old. I have no idea if it's been fixed in later kernels (and you didn't say what version of Ubuntu you're using).

---

