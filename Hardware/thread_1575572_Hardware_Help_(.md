---
title: "Hardware Help :("
date: 2010-09-15
forum: Hardware
---

### Post by illusionist1324 on 2010-09-15
Hi everyone.

Recently some people over the internet convinced me to try ubuntu. I installed it, it looks nice, but the only thing that works right now is internet.

While I don't care about every single hardware driver that is on my machine, I am hoping to have at least the graphic card (right now my resolution is very, very low - a big deal breaker) and perhaps audio (although I won't die if my computer is completely silent). 

Let me tell you what hardware I got and what I have tried so far. 

- The "Hardware Drivers" from the menu does not yield me any drivers;
- My desktop uses a GTX 460. I have downloaded the driver (Linux version) from their website, which gives me a *.run file. Unfortunately I am not sure how to run it. 
- Audio is on my Gigabyte GA-870A-UD3. Apparently there isn't any Linux support on it (which is why I have a feeling that it might never work) and I am not sure what to do with it.
- Random googling didn't do me too good :(


Thanks for reading. :D

---

### Post by Fafler on 2010-09-16
The Hardware Drivers dialog /should/ present the correct version of the Nvidia driver for your system, but maybe it doesn't know about the 460 yet. The one from the Nvidia site takes a but more work, as you'll need to install a lot of other tools to be able to use it. 
This should be able to help you out: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Sound is probably just an update or two away. Or you could try looking at the ALSA wiki. Identify your chip and look for different mixer options. It's a common problem.

---

### Post by cascade9 on 2010-09-16
The GTX 460 needs 256.44 or higher drivers, and as far as I can tell 10.04 only has the 195.x drivers, at least for now. 

10.10 already has the 256.53 drivers, so thats an option. So it manually installing the 256.44/53 drivers. There might be some PPA that has the 256.44 dribvers for 10.04, but I dont know anything about that. 

ALSA 1.0.22 (and higher) should have support for the ALC892 on your motherboard- 

> ALSA: hda - Add ALC661/259, ALC892/888VD support 

[http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22](http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22)

Alsa 1.0.22 should be in 10.04 already. 

Are you using an older ubuntu release?

---

### Post by Thomson072 on 2010-09-17
I have that motherboard with sound that doesn't work too :(. My Google-ing how to fix that got me here...

---

