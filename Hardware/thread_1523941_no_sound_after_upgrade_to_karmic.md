---
title: "no sound after upgrade to karmic"
date: 2010-07-04
forum: Hardware
---

### Post by mosaik on 2010-07-04
Hi,

sound was working on my laptop (ubuntu 7.04?). Since an upgrade to ubuntu 9.10 sound is not working any more. Settings look ok. Any hints how to proceed?

thanks,
Wolfgang

some system info:

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Motorola Si3054
Codec: Realtek ALC883

$ cat /proc/asound/card0/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC883 Analog
name: ALC883 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

---

### Post by lidex on 2010-07-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by mosaik on 2010-07-06
Hi,

I bought my laptop from [www.mingos.nl](www.mingos.nl) about 3 years ago; there is a label "AHTEC" on top.

Invoking your command list shows the following outputs:
uname -a gives:
```
Linux my-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/linux
```

aplay -l gives:
```
**** List of ..
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

dpkg -l | grep "alsa" gives:
```
ii  alsa-base    1.0.20+dfsg-1ubuntu5
    ALSA driver configuration files
ii  alsa-utils   1.0.20-2ubuntu6
    ALSA utilities
ii  bluez-alsa   4.51-0ubuntu2
    Bluetooth audio support
ii  gstreamer0.10-alsa   0.10.25-2ubuntu1.2
    GStreamer plugin for ALSA
ii  libesd-alsa0 0.2.41-5
    Enlightened Sound Daemon (ALSA) - Shared lib
ii libsdl1.2debian-alsa  1.2.13-4ubuntu4
    Simple DirectMedia Layer (with X11 and ALSA
```

head -n 1 /proc/asound/card*/codec#* gives
```
==> /proc/asound/card0/codec#0 <==
Codec: Motorola Si3054

==> /proc/asound/card0/codec#1 <==
Codec: Realtek ALC883
```

Does that give any clues?
Thanks,

Wolfgang

---

### Post by lidex on 2010-07-06
One more:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

And try this:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

