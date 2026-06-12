---
title: "HOWTO: Creative X-Fi 5.1 USB (SB1090) on 15.10 (Update to old thread)"
date: 2016-02-03
forum: Hardware
---

### Post by Kale_Freemon on 2016-02-03
This is a modern update to the old thread [HOWTO: Creative X-Fi 5.1 USB (SB1090) on 8.04 and 9.04]("http://ubuntuforums.org/showthread.php?t=1193063") that will work on Ubuntu 15.10, for those of you who may be curious as I was.

I understand it's an older piece of hardware, however its an affordable way of installing a sound card for an old laptop that doesn't have a working speaker or audio output like my old Gateway NV69C.

All you need to do for 15.10 is to install the following packages.

```
[COLOR=#000000]*sudo apt-get install libasound2-plugins pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-lirc pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils paman paprefs pavucontrol pavumeter libao4*[/COLOR]
```

Then plugin the device, go to your sound settings, and select the device (Analog Output - SB X-Fi Surround 5.1) as the output.

That's all you have to do to get this device working on 15.10 now.

---

### Post by Vladlenin5000 on 2016-02-03
Thanks :-)

---

