---
title: "Toshiba Sound"
date: 2010-01-14
forum: Hardware
---

### Post by Jookia on 2010-01-14
Hey guys, I have a laptop (Toshiba) and installed Ubuntu 9.10 on it. A problem is that it has no sound. lspci doesn't show anything and GNOME's sound mixer isn't showing any devices. It's using ALSA.

```
	$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
	$ cat /proc/asound/card0/codec#* | grep Codec
Codec: LSI Si3054
Codec: Realtek ALC861
```

Alsa wants to use the ATI HDA sound capture for some reason.

---

### Post by Jookia on 2010-01-16
Sorry for the crap bump, but I need this fixed.

---

