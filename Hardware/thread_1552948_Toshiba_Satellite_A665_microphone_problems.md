---
title: "Toshiba Satellite A665 microphone problems"
date: 2010-08-14
forum: Hardware
---

### Post by runner72 on 2010-08-14
Hello,
I recently got my mom a new laptop and put Ubuntu on it, because Windows is such a pain! I have almost everything she needs loaded onto it, including Skype, which is important because this is the first year that both my sister and I will be away at college. To make a long story short, this is how I discovered that the microphone is not working at all. I've gone into synaptic and installed all of the "tosh" packages like I read on another thread.

Here is some output from my console, I thought these outputs might be useful:
```
beth@beth-laptop:~$ uname -a
Linux beth-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
beth@beth-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
beth@beth-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
beth@beth-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI

```

Could anybody tell me how to get this microphone working?

Thanks,
~Ryan

---

### Post by Marcelo Ruiz on 2010-08-14
I'm not an expert, but I had a similiar problem with a Toshiba M640.
Try to go to the realtek website and download the latest alsa pack: realtek-linux-audiopack-5.15
Follow UBUNTU instructions in the README file to install it.
I hope it helps!

Marcelo.

---

### Post by runner72 on 2010-08-16
Hey thanks for the tip, but I can't seem to find the driver on the website! Would you happen to be able to send me a link?

---

