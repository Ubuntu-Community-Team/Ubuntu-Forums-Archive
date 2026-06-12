---
title: "Audio dies in hp dv7t on Ubuntu 9.04"
date: 2009-07-14
forum: Hardware
---

### Post by IConrad01 on 2009-07-14
First of all; hello to you all, and thank you for your time/attention.  If this is the inappropriate place to make this post, I apologize.

That being said;  I have successfully installed the current snapshot of ALSA as a kernel module -- as has been found to be a solution to the sound problem elsewhere on these forums.

I have since, however, run into a new issue with my audio and do not know what to make of it.  After a variable amount of time (sometimes five minutes, sometimes an hour), the audio just dies.  And nothing short of a full system reboot will restore it.  I have tried restarting ALSA and Pulseaudio, both to no avail.  (And both simultaneously).

I'm afraid I don't know enough to diagnose this problem.  If anyone reading this has any suggestions for resources -- or, miracle of miracles, a solution -- I am all ears. :D

Again; thank you for your time and attention.

---

### Post by KevlarSoul on 2009-09-12
Anyone? I have the same problem. No Sound. DV7T-1000 Laptop made by HP.

> work@work-laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> work@work-laptop ~ $ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD71B7X
Codec: Generic 10de ID 6


---

### Post by KevlarSoul on 2009-09-12
Found the solution:

[http://ubuntuforums.org/showpost.php?p=6068909&postcount=26](http://ubuntuforums.org/showpost.php?p=6068909&postcount=26)

> **remu said:**
> Alright folks, good news! The audio situation is solved for anyone using the IDT 92HD71B7X audio codec. Comes in most HP dv4, dv5, and dv7 laptops. The solution as found here: 
[https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

The solution is quite simply.
First:
```
gksu gedit /etc/modprobe.d/alsa-base
```

Then add the following to the end of the file:
```
options snd-hda-intel enable_msi=1
```

For me this worked on a clean install of Intrepid. Also, make sure you remove any kernel options you put in place to get sound working previously, such as noacpi, pci=noacpi, or irqpoll.
Since two of those reduce you down to one core, and the last one screws around with trackpad response.

The above mentioned solution seems to fix all my flaws, and now I seem to have everything I need working on my dv4.

Hope this helped most people.

---

