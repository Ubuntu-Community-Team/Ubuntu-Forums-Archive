---
title: "Sound Device suddenly disappeared from &quot;Sound Preferences&quot;"
date: 2010-06-15
forum: Hardware
---

### Post by lucacerone on 2010-06-15
Hi guys,
I'm having a problem with Ubuntu 10.04 on my HP Pavillon DV6000.
Till yesterday everything was working fine, today I've just realized that
the sound is no longer working. 
I've tried to see in the "Sound Preferences" which might be the problem
and I realized that the sound hardware is no longer detected.
Till yesterday I could choose between different input and output device,
but today no hardware is present and no profile can be chosen for input and output (In output appears a "greyish" Dummy Device).
Yesterday I've tried to install OSS, but everything seemed to have worked fine. I've no idea what I should look or change!

Any advice would be gratefully accepted!!!
Thanks in advance,

Cheers, -Luca

---

### Post by lucacerone on 2010-06-15
For those of you that are interested I solved the issue in the following manner:
I removed using:
sudo apt-get remove oss4-*
sudo apt-get autoremove
sudo apt-get autoclean

After that I removed alsa-player
sudo apt-get remove alsa-player

From synaptic I removed completely the packages related to alsa and oss that still had some configuration files (found using the filter STATUS -> not removed).

I then installed alsa-firmware-loader
and installef again alsa-player alsa-base and the "ubuntu" marked packages related
to alsa.

After completing and restarting the sound is now working.
Probably is not the best solution, but it's been effective.
Cheers, -Luca

---

