---
title: "Headphone sense doesn't working"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by nawitus on 2007-10-07
My headphone jack sense is not working on HP Pavilion DV6544eo laptop. I've tried about 4 different alsa versions, and currently using the latest dev version. There is no "headphone jack sense" in volume controls. I've tried to add like 10 different snd-hda-intel model in alsa-base, but doesn't resolve the issue. 
     The problem is there with both 7.04 and 7.10. I've tried to "unplug, mute, plug, unmute" trick but it doesnt work. I've tried to boot both without plugged in headphones and plugged in, but doesn't make a difference. I've tried to enable and slide all possible combinations in volume control, alsamixer, alsamixergui and whatnot, they all affect both headphone and speakers.
    The problem is that I get always sound from speakers, even when headphones are plugged in.

I have installed the latest alsa-lib, alsa-driver and alsa-utils. Doesn't fix it.

Codec: Conexant CX20549 (Venice)

```

nawi ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Crenfinkle on 2007-10-07
I know you've tried all of the "model=" options, but I literally just fixed this last night with one you may not have tried (and the same frustrating Conexant chipset).

In your alsa-base file, add "model=laptop" and "position_fix=1"

I tried model=laptop before to no avail, so position_fix=1 is definitely the one that solved the problem for me with this odd sound configuration. If that doesn't work perhaps try position_fix=3 or some other possible option for that parameter. I remember reading some output weeks ago where it looked as though the software was aware of the headphone jack, just not "listening" in the right place. 

I'm probably pretty far off the mark with my explanation, but try the fix! :)

---

### Post by nawitus on 2007-10-08
Thank you SO MUCH! It works now! :) That was my last major problem with Ubuntu.

---

### Post by BoomShaka on 2007-10-16
Hi

Sorry to be a pain, I was hoping you could guide me a little more specifically with this solution ;)

How do I specify these params:
options snd-hda-intel model=laptop position_fix=1
Is that correct?
Could you give me the exact line to add, also do I need to restart the machine (or restart X) to get this active?

Any help much appreciated.

Thanks
Boom

---

### Post by Crenfinkle on 2007-10-16
Assuming that you are using the same chipset that would be the correct line to add. After you add that line, restart the machine and give it a try!

---

### Post by BoomShaka on 2007-10-17
Ok, I tired that, but no dice. I guess I use a different chipset.
I also went through the process of upgrading alsa to the latest release version. 1.0.14 -> 1.0.15
After this my headphones ceased to work at all. hehe

I will continue to scour the interwebs in search of the heaphone-jack-holy-grail.
This seems like quite a common problem to me, I find lots of people reporting this bug, but not many solutions to it.
I am kinda holding out for Gutsy in the hope that it fixes this (I will be doing a clean install and destroying my Vista dual boot :) ).

---

### Post by ogee on 2007-11-10
Crenfinkle: many thanks for your tip. I had recompiled alsa from 1.0.14 to 1.0.15 and had no joy but then I added the "options snd-hda-intel model=laptop position_fix=1" line and all is well. One step closer to putting M$ on the garbage heap.
ogee

---

### Post by sansps on 2007-11-20
> **Crenfinkle said:**
> I know you've tried all of the "model=" options, but I literally just fixed this last night with one you may not have tried (and the same frustrating Conexant chipset).

In your alsa-base file, add "model=laptop" and "position_fix=1"

I tried model=laptop before to no avail, so position_fix=1 is definitely the one that solved the problem for me with this odd sound configuration. If that doesn't work perhaps try position_fix=3 or some other possible option for that parameter. I remember reading some output weeks ago where it looked as though the software was aware of the headphone jack, just not "listening" in the right place. 

I'm probably pretty far off the mark with my explanation, but try the fix! :)


Hi,
the solution just worked for me. I have a compaq presario c713TU laptop and 'aplay -l' gives the following result
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks a lot.

---

### Post by zirtik on 2008-02-01
Adding that line worked for me as well! Thank you! I am using HP Pavillion dv2615nr with the same chipset above. Now the only thing left is to set up my wireless card.

---

