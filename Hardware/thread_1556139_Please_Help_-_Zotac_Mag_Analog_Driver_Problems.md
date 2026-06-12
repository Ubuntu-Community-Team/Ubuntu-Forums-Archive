---
title: "Please Help - Zotac Mag Analog Driver Problems"
date: 2010-08-19
forum: Hardware
---

### Post by bob1234 on 2010-08-19
Hi Everyone. I have been digging around on and off for a year trying to get my sound card to work properly. I think it is time I asked for some help.

I have a Zotac Mag and I am interested in hooking up a pair of analog speakers to the stereo jack on the front of the box. Unfortunately the analog output has lots of noise. Let me try to explain better:

-When turning on the speakers make a popping noise. I have identified this popping feature as the sound card going into or coming out of low power mode. Since the power mode switches every time you play something, this is very annoying and can potentially damaging to the speakers.

- When you change the volume on the speakers, there is a rumble. I have tried several sets of speaks and they all seem to behave the same way. 

- The sound sounds a bit garbled. 

I do not think it is the hardware problem because I have 2 Zotac Mags that both exhibit the same symptoms. 

I am running Mythbuntu 10.04. If anyone could help I would be so happy. The box was supposed to be linux compatible. Here are my sound card details:

aplay -l :

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

arecord -l :

```
*** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


cat /proc/asound/cards : 
```

0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfae78000 irq 22
```

cat /proc/asound/modules : 

```
0 snd_hda_intel
```

---

### Post by bob1234 on 2010-08-21
Bump, Can anyone help, any suggestions?

---

### Post by Tasu on 2010-11-13
> **bob1234 said:**
> Bump, Can anyone help, any suggestions?

I'm experiencing the same problems, plus a loud bump-like noise whenever the zotac shuts down or starts up, since I installed XBMCLive on it (based on Ubuntu 10.04), I'm trying to figure out a solution even on xbmc forum, if something good is found I'll report back here!

---

### Post by Rooster242 on 2011-07-20
I'm using XBMCLive and the audio output is very low. Got speakers with an active sub hooked up the the analog out. I have another zotac using the optical out and it sounds fine. I'm not hearing the popping or rumbling noises, just really low volume.

---

