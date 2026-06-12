---
title: "nVidia Driver - how to enable PowerMizer in Desktop mode?"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by GordonFreeman on 2008-04-07
Hi,
I'm using the 169.12 forceware on my xubuntu 7.10.
The details of my graphics card:
> 
nvclock --info
-- General info --
Card:           nVidia Geforce 8600M GT
Architecture:   G84 A2
PCI id:         0x407
GPU clock:      513.000 MHz
Bustype:        PCI-Express

-- Shader info --
Clock: 1188.000 MHz
Stream units: 32 (11b)
ROP units: 8 (11b)
-- Memory info --
Amount:         256 MB
Type:           128 bit DDR3
Clock:          702.000 MHz

-- PCI-Express info --
Current Rate:   16X
Maximum rate:   16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 50C


As you can see it runs at full speed although I'm doing nothing but surfing a bit (and no I don't have a fancy 3d desktop). In the nvidia x server settings it displays as Performance Mode "desktop", is there a way to activate the throttling in desktop mode, too?

I don't know if this is important, but I'm using an external TFT (22") over HDMI.



Thanks.

---

### Post by kekc on 2008-05-27
Hi, I have also the same issue.

All I found in web is PowerMizerLevel option, that only works without power for me:
```
Option "RegistryDwords" "PowerMizerLevel=0x3"
```
there 0x1 is performance, 0x2 balanced and 0x3 powersave.

I don't know how to change "Performance Mode: Desktop" to something like "throttle".
:confused:

---

### Post by gloryplastic on 2008-05-27
I got this problems weeks ago, and I moved my PC to the seller again :)

---

### Post by hendrikwout on 2008-06-01
Same here. That option only works when running on battery :(

---

### Post by motin on 2008-06-26
nvclock seems not to show the relevant information at least not for me. nvclock always shows an output similar to yours, but in nvidia-settings -> PowerMizer, the current performance level is shown, which goes down to . 

However... as my GPU temp always exceeds 53 degrees celsius I am not to far from believing that maybe my GPU is in fact running at full speed all the time as nvclock indicates, despite with nvidia-settings reports. 

I am very interested in ways to lower my GPU temp, be it activating "Desktop" mode on demand (instead of "Maximum Performance" which seems to be the default when using Compiz), underclocking 3D Performance using CoolBits ([http://aldeby.org/blog/index.php/enable-nvidia-coolbits-frequency-tuner.html](http://aldeby.org/blog/index.php/enable-nvidia-coolbits-frequency-tuner.html)) or by other methods. 

If you have any suggestions I'd be happy to hear them. 

Cheers!

---

