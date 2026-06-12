---
title: "Soundblaster x-fi xtreme audio PCIe no sound"
date: 2009-11-23
forum: Hardware
---

### Post by alexacrimony on 2009-11-23
Well I have read the past posts about this but they seemed pretty old and I couldn't find a modern or an up to date solution on the problem. I know it has to do with the ALSA drivers but I tried almost everything and I still get no sound. Well I tried the main things that were mentioned in the past posts/stickies about this and well didn't turn out soo well since they were kind of outdated. 

Alright so I was just wondering, I have a SoundBlaster X-FI Xtreme PCI-Express sound card and all I want to do for now is to get the sound working. I'm learning ubuntu again/refreshing my memory with linux since I work in a internet cafe and some computers come in with Ubuntu installed (Dell Laptops/Desktops mainly). So help guys :] thanks.

OH and here's a pic of the exact card I have if some of you don't know which one I'm talking about. 

[http://www.dclstore.co.uk/images/products/creative-sound-blaster-x-fi-xtreme-audio-pci-express-sound-card-96-khz-70sb104000001-l.jpg](http://www.dclstore.co.uk/images/products/creative-sound-blaster-x-fi-xtreme-audio-pci-express-sound-card-96-khz-70sb104000001-l.jpg)

Most of the solutions that I've read about the sound not working was for the fatality cards and I don't have that. I just have that ^. 

Thanks :D and help would be really appreciated. This is basically all I need since I never had this problem before when I had integrated sound on my old Dell Dimension 3000 haha.

---

### Post by kostkon on 2009-11-23
If you are using 9.10, then try installing the package
```
linux-backports-modules-alsa-karmic-generic
```
and then reboot.

If you are using an older version (or if the above package will not work), then you'll need to download and install the ALSA driver yourself.

---

### Post by alexacrimony on 2009-11-23
am i supposed to type THAT exact thing? or do I put in sudo before that code?

---

### Post by kostkon on 2009-11-23
Just search for this package in *Synaptic* and install it, or if you want to install it in using the terminal, just give:
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

---

### Post by Trifidlebock on 2009-11-24
Did this work for anyone.?  Not me.

---

### Post by alexacrimony on 2009-11-25
this didnt help me at all. it just made my graphics all messed up and had to re-install ubuntu.. nice job. does anyone ELSE have a solution?

---

