---
title: "USB Sound card hell"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by The Warlock on 2005-09-03
I have an external USB soundcard (Audigy 2 NX) for my laptop. Now, this card is not always connected to my laptop (e.g. when I'm away from my desk, I don't bring it with me). 

Right now I can't seem to play to it at all, only to onboard sound. I'd like it to default to the USB card when it's there and to use onboard when it's not. Is there any way to do this? I've tried changing snd-ac97-codec (the driver for the onboard card) to -2 (in /etc/modutils/alsa-base/), but then whenever I don't have the USB card connected, my laptop beeps a whole bunch of times during boot and then I get no sound at all.

Right now my /proc/asound/cards looks like this:

```
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC655 at 0xe800, irq 18
1 [NX             ]: USB-Audio - SB Audigy 2 NX
                     Creative Technology Ltd SB Audigy 2 NX at usb-0000:00:03.3-3.2, full speed
```

The weird thing is, back when I used Debian (sarge) the USB-Audio defaulted to index 0 instead of index 1. (I had other problems with Debian that led me to switch to Ubuntu). 

Anyway, any help would be appreciated.

---

### Post by WMCoolmon on 2005-09-04
This is a common problem, and I'm hoping it's fixed in ALSA 1.0.9 (According to the person who closed the bug on ALSA mantis, it is, but I tried a Breezy kernel with 1.0.9 and it did not work.)

Here's a solution that would be best, aside from native support(But it won't work for me):
[http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2](http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2)

and a guide by me that should get it working under ALSA/esd:
[http://www.ubuntuforums.org/showthread.php?t=21882&highlight=audigy+nx](http://www.ubuntuforums.org/showthread.php?t=21882&highlight=audigy+nx)

I should point out that neither gets it working as well as it should, if you're serious about sound you should probably try to install Windows. Linux's sound support seems needlessly convoluted and woefully undersupportive of devices like the NX; I'm not sure if 5.1 will even run properly.

---

### Post by The Warlock on 2005-09-07
[QUOTE=WMCoolmon]This is a common problem, and I'm hoping it's fixed in ALSA 1.0.9 (According to the person who closed the bug on ALSA mantis, it is, but I tried a Breezy kernel with 1.0.9 and it did not work.)

Here's a solution that would be best, aside from native support(But it won't work for me):
[http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2](http://www.eng.uwaterloo.ca/~dtay/linuxLaptop.shtml#sound2)

and a guide by me that should get it working under ALSA/esd:
[http://www.ubuntuforums.org/showthread.php?t=21882&highlight=audigy+nx](http://www.ubuntuforums.org/showthread.php?t=21882&highlight=audigy+nx)

I should point out that neither gets it working as well as it should, if you're serious about sound you should probably try to install Windows. Linux's sound support seems needlessly convoluted and woefully undersupportive of devices like the NX; I'm not sure if 5.1 will even run properly.[/QUOTE]

I followed those directions on the second page, and it worked as long as the card was plugged in, but when it wasn't (when my laptop was on the go, for instance) I get system beeps while booting and then no sound.

And the only thing I use 5.1 for would be my games, which I play under Windows as it is. It just would be nice to be able to listen to music on my good speakers while coding and stuff.

---

