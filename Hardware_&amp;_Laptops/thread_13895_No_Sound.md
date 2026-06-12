---
title: "No Sound"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by fsman on 2005-02-03
Moving from Mandrake to Ubuntu, really keen to go pure Gnome.

Problem is that sound is not working at all.
I have a Asus A7M266 mb with onboard Cmedia® CMI8738 audio (this is disabled in the BIOS).
I also have SB Live on the PCI bus.

Gnome Device Manager detects both devices, however I'm getting no sound through SB Live. (Haven't tried on board - too much like hard work)

How can I get Ubuntu to use the SB Live device rather than the onboard - will that work?

---

### Post by malegria on 2005-02-05
I suggest downloading the latest ALSA drivers and compiling them.
To compile them you will need to get the source for your kernel (found in Synaptic)
So that when you run './configure' it should look like:
```
./configure --with-kernel=/usr/src/your_kernel_source
``` 

Also install alsa-utils via Synaptic. 

Run:
```
sudo alsaconf
``` 

Then run: ```
alsamixer
``` 
And raise all the necessary volumes (NOT TOO HIGH, or else you might blow out your speakers!!)

---

