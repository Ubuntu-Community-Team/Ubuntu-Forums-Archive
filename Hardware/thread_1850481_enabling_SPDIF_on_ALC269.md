---
title: "enabling S/PDIF on ALC269"
date: 2011-09-26
forum: Hardware
---

### Post by dlbogdan on 2011-09-26
Hello

I have a working EEEPC 900HA motherboard (It's an Intel Atom based low power netbook motherboard) that I want to use as a logitech squeeze slave player. 
The motherboard uses an Intel HDA codec ALC 269 witch Asus decided (of course) to cripple and not enable the chipset supported S/PDIF function.
I have soldering skills (and some brains) and enabled the S/PDIF COAX from the ALC269 chip with a few SMDs and wires.
Unfortunately this ends here for me because I can't figure out how to enable the driver part so that ALSA will enable the IEC958 Digital Output. 

Here's the output of my alsa-info.sh script:
[http://www.alsa-project.org/db/?f=233a9f92efcbb94272d1b426387c0fe1b7b1d6e7](http://www.alsa-project.org/db/?f=233a9f92efcbb94272d1b426387c0fe1b7b1d6e7)

From what I've read, the BIOS sets some "pins" configurations for the sound card and the linux driver snd_hda_intel configures the mixer for output.
I've been playing with some module parameters such as model option to no avail, I think there's a bit more to play with (such as user_pin_configs / driver_pin_configs) but I don't know where to start looking for variants.
So help me out guys, where should I look for this info? The bottom line is that the ALC 269 sound chip supports S/PDIF, but the driver refuses to acknowledge the existence of it (Because of the BIOS telling it so). I want to override that!
Anything useful will be greatly appreciated, even some other forum to place the question, anything.

Thank you in advance,
Bogdan.

---

