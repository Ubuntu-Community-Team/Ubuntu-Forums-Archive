---
title: "Low sound"
date: 2014-03-13
forum: Hardware
---

### Post by Macamba on 2014-03-13
Since upgrading to Ubuntu 13.10 I have problems with low volume. At first normal sound level returned with something of a bang. That does not happen any more. I can boost sound level past 100 % using the sound applet, but that results in bad sound quality. I tried 'alsamixer, but headphone was already on 100 %, and master was at about 85%. I turned master (and all other possible sound bars) to 100 %, but no joy. What are my options?

I have an AMD system with onboard sound card. 
```

macamba@Hermod:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

