---
title: "no hdmi sound output - GeForce 9200M GS"
date: 2011-01-11
forum: Hardware
---

### Post by Awareness on 2011-01-11
My laptop have a GeForce 9200M GS. the video output is ok but the sounds is still in the computer

```
$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: STAC92xx Analog [STAC92xx Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: STAC92xx Digital [STAC92xx Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Can anybody help me with this?

thank you

---

### Post by mikewhatever on 2011-01-12
Try opening the Sound Preferences, Hardware tab, and switching to hdmi output manually.

---

### Post by Awareness on 2011-01-12
Thanks for the help. I tried that, with no luck.

both of them:
DIGITAL STEREO (HDMI) output 
DIGITAL STEREO (HDMI) output + ANALOG STEREO input

I also tried all the other options along with those and its the same.

In alsamixer I also have several S/PDIF columns

I can unmute them, but the volume is 00 in all of them and I cant increase volume.

Any other ideas or stories of success?

---

### Post by mikewhatever on 2011-01-12
OK, did you use the 'm' key to unmute the s/pdif entries in alsamixer?

---

### Post by Awareness on 2011-01-12
> **mikewhatever said:**
> OK, did you use the 'm' key to unmute the s/pdif entries in alsamixer?

yup. But if i press up, it does not increase the volume and remains  in 00. I can change other volumes without problem

---

### Post by Awareness on 2011-01-14
bump! :D

---

### Post by mschering on 2011-01-15
I have the same problem. I remember it used to work on 10.04. Maybe that helps someone with finding a solution.

---

### Post by mikewhatever on 2011-01-17
Here is something that may provide an explanation, though not a fix.

[http://www.winmatrix.com/forums/index.php?/topic/21672-help-with-nvidia-geforce-9200m-gs/](http://www.winmatrix.com/forums/index.php?/topic/21672-help-with-nvidia-geforce-9200m-gs/)

> Nvidia's mobile graphics cards don't have audio output.

---

### Post by Awareness on 2011-01-17
> **mikewhatever said:**
> Here is something that may provide an explanation, though not a fix.

[http://www.winmatrix.com/forums/index.php?/topic/21672-help-with-nvidia-geforce-9200m-gs/](http://www.winmatrix.com/forums/index.php?/topic/21672-help-with-nvidia-geforce-9200m-gs/)


thank you! It never occurred to me to search with windows . I thought it worked on windows. I hadnt tried since I dont have any windows around :S

I did had thought about the jack thing, but then on second thought, I realized it was a bad idea, since I have to set the tv to hdmi and It wouldnt be able to find the sound input via av :S

bummer. :(

I someone discover anything aside from connecting the headphones jack to a separate sound system, tell me about it ;)

---

### Post by mschering on 2011-01-27
but it works on ubuntu 10.04!

---

### Post by mschering on 2011-01-27
I finally found a solution. Go to System -> Restricted drivers and select the older Nvidia 173 drivers. Then audio is working fine!

---

### Post by Awareness on 2011-01-28
> **mschering said:**
> I finally found a solution. Go to System -> Restricted drivers and select the older Nvidia 173 drivers. Then audio is working fine!

Really?  I havent tried in a year or 2 the hdmi output. I have to try that older option.

The only problematic part its that its not my laptop. The owner is not very good with computers and i cant risk to change the graphics driver from distance :(

I wont see her again in another 6 months at least...I hope to remember next time i see her... 

Thank you very much btw!!

Latest nvidia drivers also dropped support for my desktop pci nvidia card :(

wtf nvidia... wtf... :(

---

### Post by BluePhase on 2011-03-07
I'm using the nVida 173 drivers, but when I check my output choices within sound I dont have a HDMI option, any ideas?

When i check aplay -l it does show a HDMI option

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by babusar on 2011-09-06
I used this link to get audio running through hdmi:
 
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller)

I'm running a eMachine ER1401 with a GeForce 9200. It works spot on now!

---

