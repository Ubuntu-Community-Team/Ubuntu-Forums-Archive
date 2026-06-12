---
title: "Sound Card Driver issue"
date: 2013-12-09
forum: Hardware
---

### Post by aiden.aston on 2013-12-09
Hey guys wonder if you could help me,

I downloaded and installed Ubuntu on my laptop a few months ago and I could never get my sound card to work - so I downloaded the drivers from the manufacturers site after finding out that they weren't installed. After download I tried to run but it was an .exe file and wouldn't. I have since downloaded WINE and other windows compatibility softwares all to no avail.

Is there any way for me to install the drivers that you can think of?

Thanks,

Aiden.

---

### Post by ajgreeny on 2013-12-09
We need much more info about the sound card that you are using; most sound cards work in ubuntu without the need for further action or driver installation, and there is no way that you can use a driver running through wine for the OS itself.

If you are not sure abut the card in your machine show us the output of ```
aplay -l
``` in terminal (lower case L at the end, not figure 1)

---

### Post by aiden.aston on 2013-12-10
I get.

card 0: Intel [HDA Intel], Device 0: STAC92xx Analog [STAC92xx Analog]

subdevices: 0/1
subdevice #0: subdevice #0

---

### Post by ajgreeny on 2013-12-10
You should not need any drivers for an Intel sound card, so I think we need to look a little closer at your sound settings.

Open up the pulseaudio volume control to check how the levels are set in that.

Also use command **alsamixer** in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by aiden.aston on 2013-12-13
Sorry once again for the late reply.  Settings are set to high as they'll go. But according to alsamixer I have no available speakers or soundcard?

---

### Post by ajgreeny on 2013-12-13
If you have any .wav files on your system try playing them with ```
aplay *filename*.wav
``` from the folder containing the wav file.

What happens then?

---

### Post by Yellow Pasque on 2013-12-13
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

