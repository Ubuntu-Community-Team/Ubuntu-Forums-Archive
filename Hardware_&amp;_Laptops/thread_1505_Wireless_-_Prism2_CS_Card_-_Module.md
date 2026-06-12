---
title: "Wireless - Prism2 CS Card - Module ?"
date: 2004-10-21
forum: Hardware &amp; Laptops
---

### Post by radio on 2004-10-21
Hi,

i successfully managed to install the ubuntu-release on my laptop computer.

My wireless card was not detected however. Its an Allnet CS (Compact Flash) Device, i had it running under Gentoo by using PCMCIA-CS together with the linux-wlan-ng package, which provided the prism2_cs module which is needed to operate the card.

I installed the pcmcia-cs package and the linux-wlan-ng package by using synaptic. locate says there is still no prism2_cs on the system. dmesg shows that its trying to talk to the card by using the orinoco_cs module which doesnt work of course.

Now I am a little stuck. I suppose I have to install the kernel-sources and compile the module myself ? Or is there a different way of getting the card to work ? I would like to know what the ubuntu-way of doing this is before I start.


radio.

---

