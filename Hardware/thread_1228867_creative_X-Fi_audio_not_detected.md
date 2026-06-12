---
title: "creative X-Fi audio not detected"
date: 2009-08-01
forum: Hardware
---

### Post by ronan_56 on 2009-08-01
Hey!

I have just bought creative sound blaster X-Fi audio(chipset CA0106). I have installed the module, but it s not detected by alsa. 

It's detected with lspci:

> 
ro@rico:~$ lspci| grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

But not by alsa:

> 
ro@rico:~$ asoundconf list
Names of available sound cards:
Intel

ro@rico:~$ cat /proc/asound/modules
 0 snd_hda_intel


i guess there is some configuration file to modify. But I don't know which one and how. 
I have tryed to follow that [wiki]("http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106") But it s still not working.

Can anyone help me up

---

### Post by ronan_56 on 2009-08-02
up

---

### Post by ronan_56 on 2009-08-03
Any idea?

The output of the comand aplay -l is little weird:

> ro@rico:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And of course no ca0106 card detected.. (only the motherboard chip)

---

### Post by rcayea on 2009-08-04
I don't mean to jump on your thread, but I wanted to bump it because I have the same exact situation. Maybe someone out there has some ideas?

---

