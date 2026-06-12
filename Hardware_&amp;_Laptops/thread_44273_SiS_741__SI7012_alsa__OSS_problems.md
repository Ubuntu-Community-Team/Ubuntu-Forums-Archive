---
title: "SiS 741 / SI7012 alsa / OSS problems"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by python_guy on 2005-06-25
Does anyone know how to solve that hardware problem? (hoary 5.04)

I have a PC with Sempron CPU and SiS 741 mother board (SiS 7012 sound chip). The esd is linked to oss but not alsa (libesd0 but not libesd-alsa0, which is not a bad thing in this system). I use xfce4 desktop.

Problem 1:
if I use alsa audio output, sometimes the audio is skipping. In that case, I would switch to OSS.
(I am using a rc alsa driver of April/May of 2005)

Problem 2:
if I use OSS audio output, the mixer is in 100% or 0%, sometimes it may give me a big shock since I use headphone.

Please drop a message if anyone could help me solving at least one problem. Thanks in advance.

---

### Post by python_guy on 2005-06-25
the first problem is probably a mplayer related problems, I see tons of alsa-space messages:

alsa-space: xrun of at least 83.587 msecs. resetting stream,?% 0 0 97%
alsa-space: xrun of at least 69.906 msecs. resetting stream.3% 1 0 96%
alsa-space: xrun of at least 105.365 msecs. resetting stream5% 2 0 94%
alsa-space: xrun of at least 93.913 msecs. resetting stream.3% 3 0 92%
alsa-space: xrun of at least 61.377 msecs. resetting stream.2% 4 0 88%

use parameter of "-af resample=48000" in mplayer help sometimes but added others problems. Unluckily, I am in 56k, so I won't compile mplayer pre7, it would take at least 4 hours in order to download the related source.

---

