---
title: "upgraded to 18.04 and lost sound"
date: 2019-03-03
forum: Hardware
---

### Post by ncsailor on 2019-03-03
I had been using Ubuntu 16.10 for quite a while.  began having problems and had to select an alternate boot and used xxx.39 to make things work.  Decided to upgrade to 18.04 (the latest LTS.  After installing I found that I have no audio.  I have tried the workarounds given elsewhere such as loading pullse, but still no sound.  When I go to the system settings, there are no sound cards visible from which to choose.  If I use alsamixer in the terminal, my sound cards show up, but neither one will produce sound.  I have posted below the results on the needed configuration requests:

```

robert@robert-L850D:~$ lspci -vnn | grep -iA5 audio
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
    Subsystem: Toshiba America Info Systems Trinity HDMI Audio Controller [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f0244000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
--
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
    Subsystem: Toshiba America Info Systems FCH Azalia Controller [1179:ff1e]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

robert@robert-L850D:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
Failed to load cookie file from cookie: Permission denied
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

robert@robert-L850D:~$ pactl list
Failed to load cookie file from cookie: Permission denied
Connection failure: Access denied

robert@robert-L850D:~$ pactl info
Failed to load cookie file from cookie: Permission denied
Connection failure: Access denied


robert@robert-L850D:~$ dpkg -l | grep alsa
ii  alsa-base                                  1.0.25+dfsg-0ubuntu5                         all          ALSA driver configuration files
ii  alsa-utils                                 1.1.3-1ubuntu1                               amd64        Utilities for configuring and using ALSA
ii  gstreamer1.0-alsa:amd64                    1.14.1-1ubuntu1~ubuntu18.04.1                amd64        GStreamer plugin for ALSA
```

If anyone might be able to point me in a direction for resolving this, I would be greatly appreciative.

Thank you,
Robert A. Williams

---

### Post by QIII on 2019-03-03
Hello!

Please include all terminal commands and their output, as well as the contents of config files and such, in code tags.  That will preserve formatting and make your posts easier to read.

To use code tags, either:

1:  Click the # button in the toolbars above the text entry area, place your cursor between the code tags that appear, then type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

2:  Type [noparse]```
[/noparse] before the text and [noparse]
```[/noparse] after it.  The square brackets are required.

Also, please do not include your email address in your posts.  First, there are web crawlers that will pick it up and you may end up with an inbox full or spam.  Second, and more important to the community, is that we do not want questions asked here to be answered privately via email.  That robs others of the ability to find solutions here in open threads and thus is disrespectful to the community.

Cheers!

---

### Post by Yellow Pasque on 2019-03-04
> Failed to load cookie file from cookie: Permission denied

It sounds like an issue with ~/.config/pulse/cookie

If it was me, I'd simply delete the entire ~/.config/pulse directory and restart pulseaudio (either kill it or log out and back in) to generate a fresh pulse config for your user.
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

