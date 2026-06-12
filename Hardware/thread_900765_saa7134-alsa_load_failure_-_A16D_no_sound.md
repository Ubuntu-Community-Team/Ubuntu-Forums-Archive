---
title: "saa7134-alsa load failure - A16D no sound"
date: 2008-08-25
forum: Hardware
---

### Post by hujer on 2008-08-25
I installed AverTV Hybrid + FM A16D TV card and updated kernel (2.6.24-19, Ubuntu) with v4l-dvb-a4843e1304e6 downloaded from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb). Both analog and DVB work excellent, but there is no sound. Dmesg shows several errors while loading audio support saa7134-alsa like:

[   51.954984] saa7134_alsa: disagrees about version of symbol saa7134_tvaudio_setmute
[   51.954987] saa7134_alsa: Unknown symbol saa7134_tvaudio_setmute
[   51.955085] saa7134_alsa: disagrees about version of symbol saa_dsp_writel
[   51.955087] saa7134_alsa: Unknown symbol saa_dsp_writel
...
and others. Saa7134 is not loaded, SAA7134 PCM [SAA7134 PCM] is not recognized (no device created) and therefore no sound is available from TV card.

Please, does anybody know how to correct (compile) new saa7143-alsa module?

Thanks in advance.

---

