---
title: "Sound driver problem"
date: 2010-07-20
forum: Hardware
---

### Post by owl_order on 2010-07-20
Hi all, after using visiting this forum for 2 years, this is my first time posting here. I've decided to post because I've tried looking for solutions and done quite a number of things but things just got worse.

I'm running Lucid 64-bit, and after initial installation, plugging earphones into the audio jack did nothing except muting the speakers (the speakers were absolutely fine). I went around the forums and installed Alsa 1.0.23 (i think, either way it's the latest version) and tweaked around with the configuration files.

And now, neither the speakers nor the audio jack works. I've checked and double-checked the Alsa mixer settings, both from GUI and command line and unmuted everything.

Little extra info. Win7 works fine, Lucid 32-bit had the exact same initial problem with 64-bit (speakers only, plugging in headphones mutes speakers, ran 'LiveCD' from USB, no installation), Karmic 64-bit plays through headphones but not speakers (from USB as well). Karmic 32-bit seemed to work fine from USB, though. I've tinkered around with /etc/modprobe.d/alsa-base.conf and I've achieved total silence on both speakers and audio jack and unresponsive audio jack (sound came from speakers regardless of whether headphones were plugged in).

I'm on Asus N82J here, which is a new model and is still not listed in [http://www.linlap.com/wiki/asus](http://www.linlap.com/wiki/asus)

Any help will be appreciated, let me know if extra information is needed.

---

### Post by lidex on 2010-07-20
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

### Post by owl_order on 2010-07-20
As mentioned, my notebook is an ASUS N82J, a new model. I guess that's why I'm having driver problems, things usually went well for me in the past.

```
yeowenqi@OO-N82:~$ uname -a
Linux OO-N82 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

yeowenqi@OO-N82:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

yeowenqi@OO-N82:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                 1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                           1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                            1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                        1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

yeowenqi@OO-N82:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC259

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT240 HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT240 HDMI



```Oh by the way, I think I should mention, the speakers have come back. I can't really recall but I think I removed all changes to alsa-base.conf file yesterday. No luck with audio jack, though.

Thanks in advance for your help. :D

---

### Post by lidex on 2010-07-20
I would suggest upgrading your alsa install via the alsa-upgrade link in my sig.

---

### Post by owl_order on 2010-07-21
I have already upgraded to 1.0.23 before posting here.

And now my Lucid is totally mute. Don't really remember doing anything. The speakers were fine this morning.

---

### Post by lidex on 2010-07-21
> **owl_order said:**
> I have already upgraded to 1.0.23 before posting here.

And now my Lucid is totally mute. Don't really remember doing anything. The speakers were fine this morning.

Obviously it didn't work.
> ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                 1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                           1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                            1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                        1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities


---

### Post by owl_order on 2010-07-22
My speakers are working again, without rolling back to the previous ALSA version. Of course, the audio jack is still not working. It's not muting my laptop speakers at this point.

---

### Post by owl_order on 2010-07-22
Nevermind, I've installed Karmic instead, the drivers work great now.

Thanks a lot for your help anyway.

---

