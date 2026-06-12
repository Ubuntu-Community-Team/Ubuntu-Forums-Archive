---
title: "Microphone problem, acer timeline x 4820TG"
date: 2010-05-19
forum: Hardware
---

### Post by giova.86 on 2010-05-19
Hy everyone. I have a problem with ubuntu 10.04 and the integrated microphone on an acer 4820tg: simply it doesn't work.
If i go in: system->preference->audio and I select the input tab I see nothing, with the output everything works fine.
I have already check with: alsamixer -V the soundlevel but the problem is that the system doesn't recognize my integrated microphone.

With ```
lspci | grep Audio
``` I obtain:
```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

Does anyone have any advise? Thank you, and sorry for my english :P

---

### Post by giova.86 on 2010-05-20
up!

---

### Post by lidex on 2010-05-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by giova.86 on 2010-05-21
Thank you for the replay. These are the output for the commands:
 
uname -a
```
Linux aizen 2.6.34-020634rc7-generic #020634rc7 SMP Mon May 10 09:08:52 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC259 Analog [ALC259 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: ALC259 Digital [ALC259 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Generic [HD-Audio Generic], dispositivo 3: ATI HDMI [ATI HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```

cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
```

head -n 1 /proc/asound/card*/codec#*
```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC259

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```

---

### Post by lidex on 2010-05-21
Follow the alsa-upgrade link in my sig to upgrade your alsa install and report your results. First make sure to uninstall alsa-backports if you have them installed.

---

### Post by glacorre on 2011-08-07
I find the solution
Open terminal
tap  "alsamixer"  a window will appear
use the TAB key
go on CAPTURE with the arrow key then tap Y until the left colonne decrease
close the window and you micro works

Note : On skype disable auto sound management

---

