---
title: "Headphones do not sound without sounding too PC speakers"
date: 2009-03-24
forum: Hardware
---

### Post by aispobla on 2009-03-24
I speak english little, but only is that, the of the title. Headphones + PC speakers o nothing. Only headphones without PC skeakers sound not is posible.

I have Ubuntu 8.10 updated. In hardy also was.

I have a laptop Asus Z53E, MB ver F3E AP151C

Thanks

---

### Post by teaker1s on 2009-03-25
This is an issue with ALSA, it has affected several versions.

Generally the recommendation is to add a model parameter if the sound card is hda_intel based, failing that the latest ALSA compiled and installed

---

### Post by aispobla on 2009-03-25
What do you recommend? I've tried several solutions and never fared well. I accept any suggestion.

id:	
multimedia
description: 	Audio device
product: 	82801H (ICH8 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
module	=	snd_hda_intel

---

### Post by teaker1s on 2009-03-25
Possibly you may find a model line may work

```
sudo gedit /etc/modprobe.d/alsa-base
```

at the end of the file you may have

> options snd-hda-intel model=[COLOR="Red"]auto[/COLOR] 

you may find that if you delete the original line then put your model line in it will help define hardware.

examples

options snd-hda-intel model=[COLOR="Red"]acer[/COLOR]
options snd-hda-intel model=[COLOR="Red"]acer-aspire[/COLOR]
options snd-hda-intel model=[COLOR="Red"]toshiba[/COLOR]

save and reboot.

This may or may not improve the situation, various versions of alsa suffer from mute speaker while using headphones.

---

### Post by aispobla on 2009-03-26
Thanks, but it did not work. Any other idea? I don't translate well speaker. I was not referring to the microphone, I was referring the speaker's (loudspeaker?) normal computer, the common.

---

### Post by teaker1s on 2009-03-26
I would expect from the patchy experiences I have had that ALSA is to blame.

You could try compiling the latest version if your understanding of compiling and configuring it is good.

 Personally if you can live with it, until the next ALSA update it may be the most hassle free option

---

### Post by aispobla on 2009-03-26
Thanks for the reply, wait. Although I have been waiting since the release of Ubuntu 7.04 and have not solved the problem.

---

### Post by teaker1s on 2009-03-26
Okay what model laptop do you have or if you are using a desktop pc what model desktop / motherboard do you have.

If you post some details I will look for any avaliable solution

---

### Post by aispobla on 2009-03-26
I have do a file lshw cuted but size. Is this enough?


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by teaker1s on 2009-03-26
this link is for gutsy but it directly explains your issue on your model notebook, possibly asking a question on launchpad may help

[https://answers.launchpad.net/ubuntu/+question/26576]("https://answers.launchpad.net/ubuntu/+question/26576")

---

### Post by aispobla on 2009-03-28
Thanks, but it did not work. I compiled also and nothing. Thanks.

---

### Post by aispobla on 2009-03-29
I found the solution:

Add in /etc/modprobe.d/alsa-base

options snd-hda-intel model=lenovo

I don't know because is lenovo, because is Asus, but with lenovo work. Found in [http://ubuntuforums.org/showthread.php?t=616845&page=12](http://ubuntuforums.org/showthread.php?t=616845&page=12) [^]

Thanks.

---

### Post by teaker1s on 2009-03-31
Glad you have found solution, I know how frustrating it can be.

Maybe you could put a note on the ubuntu community documentation site-just in case someone else has this issue.

---

