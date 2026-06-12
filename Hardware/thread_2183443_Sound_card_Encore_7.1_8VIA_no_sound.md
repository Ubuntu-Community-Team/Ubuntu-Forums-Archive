---
title: "Sound card Encore 7.1 8VIA: no sound"
date: 2013-10-24
forum: Hardware
---

### Post by rva1945 on 2013-10-24
Hi:

I made a fresh installation of 12.04 in a new partition. The sound card is working ok in Win XP, but there is no sound at all in Ubuntu.
In sound settings, I try the sound test in these three available output options (to no avail):

Digital Sound (S/PDIF)
VT1720/24[Envy24PT/HT] PCI Multi channel Audio Controller

Analog Output / no amplifier 
VT1720/24[Envy24PT/HT] PCI Multi channel Audio Controller

Analog Output / amplifier
VT1720/24[Envy24PT/HT] PCI Multi channel Audio Controller

in Input, the option
Line In
VT1720/24[Envy24PT/HT] PCI Multi channel Audio Controller

seems to work as I have a guitar plugged to the Line In jack and strumming the string makes the vumeter to show volume level.


Alsamixer doesn't show the AUTO-MUTE option, that is what I looked for as some people suggest turning this feature off. Anyway I raised all the volume controls to maximun. Here is what amixer scontrols produces:

Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Surround',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost (+20dB)',0
Simple mixer control 'Mic Select',0
Simple mixer control 'Video',0
Simple mixer control 'Phone',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Output',0
Simple mixer control 'IEC958',1
Simple mixer control 'Beep',0
Simple mixer control 'Aux',0
Simple mixer control 'Capture',0
Simple mixer control 'Mix',0
Simple mixer control 'Mix Mono',0
Simple mixer control 'External Amplifier',0
Simple mixer control 'Multi Track Internal Clock',0
Simple mixer control 'Multi Track Rate Locking',0
Simple mixer control 'Multi Track Rate Reset',0

Any hint?

Thanks,
Robert

---

### Post by Yellow Pasque on 2013-10-25
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

