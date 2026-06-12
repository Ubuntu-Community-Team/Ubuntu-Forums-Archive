---
title: "How to disable a sound card?"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by tjwhaynes on 2004-12-02
I have two sound chips in my AMD64 box. One is the onboard via82xx sound card, the other is a PCI Aureal Vortex 2 card that I had hoped to get working sooner or later.

I know that au8830 chipset driver is broken for AMD64 on Mandrake 10.1 and it's not any better on Ubuntu Warty. So I would like to disable it for now and try some troubleshooting later.

On a Mandrake box, I would simply dive into /etc/modprobe.conf and edit out the snd-au8830 module from config, run depmod -a and reboot. That doesn't seem to be the case with Ubuntu - the hotplug system seems to be driving the module loading. So how do I stop it loading the snd-au8830 module?

Thanks,
Toby Haynes

---

### Post by WW on 2004-12-05
You could try adding the module to **/etc/hotplug/blacklist**.

---

### Post by LongTooth on 2004-12-06
Why don't you just go the the Bios on boot up and disable the on board sound chip? I'm not working on equipment as new as your. I've got a PIII/550MHZ porcessor with an intergrated sound chip which Warty never recognized. I was forced to purchase an inxepensive -$15-PCI sound card. On boot-up I entered the Bios and disabled the sound chip. No problems with my add on PCI card and I has my sound.

---

### Post by daulex on 2008-01-01
> **LongTooth said:**
> Why don't you just go the the Bios on boot up and disable the on board sound chip? I'm not working on equipment as new as your. I've got a PIII/550MHZ porcessor with an intergrated sound chip which Warty never recognized. I was forced to purchase an inxepensive -$15-PCI sound card. On boot-up I entered the Bios and disabled the sound chip. No problems with my add on PCI card and I has my sound.

simple yet genious, thank you so much

---

