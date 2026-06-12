---
title: "Headphones don't work"
date: 2010-01-09
forum: Hardware
---

### Post by josephellengar on 2010-01-09
I'm using gnome and karmic 64 bit with the comp in my sig.  When I plug headphones into either of the jacks, not only does the sound not cut off from my main speakers, but the headphones don't play anything.  The computer is brand new and these headphones and these jacks work in windows.  Anybody have any ideas?

---

### Post by lidex on 2010-01-09
Can you post the output of these commands?
```
cat /proc/asound/version
```
```
head -n 1 /proc/asound/card0/codec*
```

---

### Post by buntunub on 2010-01-09
I can confirm this issue and further add that I discovered that via the default pulseaudio setup Karmic has, all sound gets routed through the headphone channel - ie. when I mute headphones via kmix or pulseaudio volume control, I lose all sound in speakers. Here is my info:


```
cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.20.

```
head -n 1 /proc/asound/card0/codec*
```

Codec: Realtek ALC888

---

### Post by lidex on 2010-01-09
If you're up to the challenge, go here and upgrade your alsa drivers.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by buntunub on 2010-01-09
Appreciate the help. Isnt it crazy that with every kernel upgrade I now have to reinstall both graphics AND audio drivers just to get Ubuntu working. What a PITA!

---

### Post by josephellengar on 2010-01-09
I had the same output as above for the first command but the second command gave the following: 
```

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

```

Should I try updating the alsa drivers as well?  Thanks for the prompt response before.

---

### Post by lidex on 2010-01-09
Can you post output of these commands please?

```
aplay -l
```
```
aplay -L
```
```
gedit /etc/modprobe.d/alsabase.conf
```

Please enclose output in code tags ;)

---

### Post by lidex on 2010-01-09
> Should I try updating the alsa drivers as well? 

Umm, yes...how many people am i talking to here?

edit: buntunub, you're on Hardy?

---

### Post by josephellengar on 2010-01-09
> **lidex said:**
> Can you post output of these commands please?

```
aplay -l
```
```
aplay -L
```
```
gedit /etc/modprobe.d/alsabase.conf
```

Please enclose output in code tags ;)

```
aplay -l
```
output: 
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
aplay -L
```
output:
```

front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```
```
gedit /etc/modprobe.d/alsabase.conf
```
no contents

---

### Post by lidex on 2010-01-09
> **rossholley said:**
> 
```
gedit /etc/modprobe.d/alsabase.conf
```
no contents

My bad, that's:
```
gedit /etc/modprobe.d/alsa-base.conf
```

Go ahead and update alsa.

---

### Post by buntunub on 2010-01-10
What about the supported alsa-backports? Would those packages work here for the upgrade? At least those support updates and such.

---

### Post by lidex on 2010-01-10
> **buntunub said:**
> What about the supported alsa-backports? Would those packages work here for the upgrade? At least those support updates and such.

Yeah -- I don't know.
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

---

