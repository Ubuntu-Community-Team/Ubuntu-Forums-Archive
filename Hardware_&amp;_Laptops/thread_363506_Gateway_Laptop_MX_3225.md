---
title: "Gateway Laptop MX 3225"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by andrewlightstar on 2007-02-17
I just installed Ubuntu 6.10 on my laptop. Everything works but the sound. The volume control works perfectly it will even mute but no sound comes out. The laptop has the AC '97 2.3 Compliant audio on board and when I check the sound preferences it has the VIA 8237 twice, ALSA, EDS and OSS, but switching between the different things doesn't help. the sound seems to be listed correctly in the /proc directly under interrupts, ioports, devices, and asound. Even the correct driver seems to be loaded in modules. Anyone faced this problem to, or any suggestions would help. Andrew.

P.S. I don't get any errors on the console when booting or trying to play sounds.

---

### Post by andrewlightstar on 2007-02-18
Not sure if anyone going to help, but I actually got the system beep to work by building in AC'97 into the Kernel. But now the sound won't unmute for the rest of the system and it won't recognize the sound card now.

---

### Post by Aaronb2245 on 2007-03-04
Hey guy,

I know this has been a headache for you as it sure was for me. I have a gateway laptop and tried everything. In the end this simple fix is what worked and will work for u I am sure.

[http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/](http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/)


Enjoy your snd. I read info on this and played with the snd religously for 1 1/2 days before I came across this info that actually worked.

Aaron

---

