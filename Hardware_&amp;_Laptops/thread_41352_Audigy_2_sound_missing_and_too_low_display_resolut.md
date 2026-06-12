---
title: "Audigy 2 sound missing and too low display resolution and Mhz rate"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by Dainius on 2005-06-13
Hello,

Just installed Ubuntu from CD, it is 5.04 version. There is not much I know about Linux or Ubuntu, so I need very detailed instructions. My two problems are:

1. No sound. Using OEM Audigy 2.
2. Too low display resolution (1024-768) and refresh rate (60Mhz). Higher options are not shown. Using NV GeForce 5900FX card.

If someone would help me with detailed instructions, I appreciate that very much. I am pretty good familiar with windows XP, but no experience of Linux (any distributions).

 :???: ,
Dainius, Vilnius, Lithuania

---

### Post by philipacamaniac on 2005-06-13
1. [http://www.ubuntuforums.org/showthread.php?t=21211&highlight=digital+analog+sound+output](http://www.ubuntuforums.org/showthread.php?t=21211&highlight=digital+analog+sound+output) 
You can try to toggle digital/analog output by opening a terminal and running:

```
sudo alsamixer
```

Then scroll over to the Audigy Analog/Digital Output Jack and change it.

2. For your Nvidia, you want to install Nvidia's driver: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by TheDude on 2005-06-13
[QUOTE=philipacamaniac]Then scroll over to the Audigy Analog/Digital Output Jack and change it.[/QUOTE]

I've had to do this before, but I can't remember how to turn it on ](*,)

---

### Post by Dainius on 2005-06-13
[QUOTE=TheDude]I've had to do this before, but I can't remember how to turn it on ](*,)[/QUOTE]

same here. trying everything ...  :neutral:

---

### Post by Dainius on 2005-06-13
[QUOTE=TheDude]I've had to do this before, but I can't remember how to turn it on ](*,)[/QUOTE]

press M  \\:D/

---

### Post by Dainius on 2005-06-13
[QUOTE=philipacamaniac]1. [http://www.ubuntuforums.org/showthread.php?t=21211&highlight=digital+analog+sound+output](http://www.ubuntuforums.org/showthread.php?t=21211&highlight=digital+analog+sound+output) 
You can try to toggle digital/analog output by opening a terminal and running:

```
sudo alsamixer
```

Then scroll over to the Audigy Analog/Digital Output Jack and change it.

2. For your Nvidia, you want to install Nvidia's driver: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)[/QUOTE]

sound solution worked, will check sound quality in the morning.

video solution let me set 1024x768 resolution. Earlier on such attempt i used to get double screen. But now this is still the highest resolution and still nothing higher that 60 Mhz refresh. Are there any more solutions for these?

And thanks very much  :grin:

---

### Post by Dainius on 2005-06-14
sound ok. video still nothing.

---

