---
title: "no sound with internal soundcard, just hdmi, how to update playback hardware devices"
date: 2019-04-08
forum: Hardware
---

### Post by enrique-costa-montenegro on 2019-04-08
Hello,

I have a laptop with Ubuntu 18.04.2. I don't have sound in my laptop, just when I use the hdmi ouput. I have two sound cards, as seen with lspci -nn | grep '\[04[80][13]\]'

```
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
```

Both soundcards are recognized and activated:

```
Sound cards recognized by the system:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)

```

When I check the playback hardware devices with aplay -l

```
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 7: HDMI 1 [HDMI 1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 8: HDMI 2 [HDMI 2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 9: HDMI 3 [HDMI 3]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: HDMI [HDA Intel HDMI], dispositivo 10: HDMI 4 [HDMI 4]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

They are only associated with the card 0 and HDMI, but none with the other card.

How can I update this playback devices in order to have sound in my laptop?

All the alsa information can be found in [URL="http://alsa-project.org/db/?f=c8a5dee8080ee4de547d8b59e47c9f69061d5fd1"]http://alsa-project.org/db/?f=c8a5dee8080ee4de547d8b59e47c9f69061d5fd1
[/URL]
Thanks for your help!

---

