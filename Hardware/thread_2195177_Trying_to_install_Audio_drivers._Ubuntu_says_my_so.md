---
title: "Trying to install Audio drivers. Ubuntu says my sound card is Intel, but it's Realtek"
date: 2013-12-22
forum: Hardware
---

### Post by richieetorres on 2013-12-22
Hello everyone!

I was wondering if there is a way to install a proper sound driver in Ubuntu for my Acer Aspire M5-581TG. 

For Windows, I install a Realtek driver to get my sound working properly. But with Ubuntu, I get an Intel Pantherpoint HDMI (HDA Intel PCH).

When I am hearing music, it sounds like I'm hearing music out of a tin can. When I listen to music, when a singer reaches a certain decibel my ears start to hurt, I actually have to turn down the volume but even at that I can still hear it and my ears hurt (using the speakers on my laptop)

I think Ubuntu is getting my HDMI port (Intel HD 4000) as my audio? I really have no clue. Even when i look at the Acer website for drivers for my laptop and there are no Intel sound drivers available for my laptop.

Can someone help me getting the audio up and running? or at least throw a control app that allows me to adjust the Equalizer?

alsamixer screenshot:
[IMG]http://i40.tinypic.com/1h6s5g.png[/IMG]


I'm currently using Ubuntu 13.10 x64 Bit.

Thanks a bunch for any help!


--ADD--

Also i am sure my audio card is Realtek because I remember that when I used Windows I was able to use Dolby Home Theater program on my laptop to make the sound sound a lot better.

---

### Post by Yellow Pasque on 2013-12-23
On Linux, it doesn't matter if it's Realtek, Conexant, IDT, VIA, etc. They all conform to Intel HDA spec, and they're all supported by one kernel module/driver (snd-hda-intel). The driver that Ubuntu uses by default is the correct one. If you're interested in obtaining latest version, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

> For Windows, I install a Realtek driver to get my sound working properly
Realtek offers Linux audio drivers specific to their codecs, but I would not recommend installing them. They never seem to help and often result in no sound whatsoever since noob's have a hard time building kernel modules.

For equalizer, you can try pulseaudio equalizer (google it) for system-wide equalizer, but I personally think it's better just to have an equalizer built into the music player. What player are you using? Rhythmbox?

---

