---
title: "Low Sound Dell Inspiron 1545"
date: 2011-09-20
forum: Hardware
---

### Post by chiraag on 2011-09-20
In comparison to the Vista install, the volume on the 10.04.3 LTS install is much lower.
I have already increased the Master and PCM to 100, but it is still lower than the Windows level. No front is visible on the controls.

[http://www.ubuntu.com/certification/hardware/200910-4252:200911-4633:200912-4896:200912-4897](http://www.ubuntu.com/certification/hardware/200910-4252:200911-4633:200912-4896:200912-4897) says I am running certified hardware. I suspect this is a solved problem.

Suggestions?

---

### Post by FerroPower on 2011-09-26
I am also using the same model but I am using the latest Kubuntu 11.10 beta version. Sound is comparatively lower then in Vista & windows 7. 

The audio files sounds much much better in windows because Dell provides Audio DRIVER's, whereas in Linux  audio either gets configured automatically or you have tweak the configuration files, but even after much tweaking the sound quality is no match to windows. 

by the way if you know how to edit Alsa conf file be sure to select "model=dell-m4-3" and also enable_msi=1. the sound will be much better then before. dont forget to unmute using alsamixer also mute all mic options if your not using it.

---

### Post by .... on 2011-09-26
Can someone post their alsa-info? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by maul9999 on 2011-09-26
> **chiraag said:**
> In comparison to the Vista install, the volume on the 10.04.3 LTS install is much lower.
I have already increased the Master and PCM to 100, but it is still lower than the Windows level. No front is visible on the controls.

[http://www.ubuntu.com/certification/hardware/200910-4252:200911-4633:200912-4896:200912-4897](http://www.ubuntu.com/certification/hardware/200910-4252:200911-4633:200912-4896:200912-4897) says I am running certified hardware. I suspect this is a solved problem.

Suggestions?

What is model of sound onboard you have right now?

---

### Post by FerroPower on 2011-09-26
> **.... said:**
> Can someone post their alsa-info? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I m using similar Dell 1545 laptop having same problem. I am attaching the Alsainfo text(uploaded as tar because the forum was giving upload limit error) with this message.

I will appreciate if you can help us.

---

### Post by FerroPower on 2011-10-07
FOUND SOLUTION in LINUXMINT (Debian)

THE SOUND ROCKS in LINUXMINT (Debian). I don't understand how Linuxmint can configure sound card PERFECTLY without any need to configure any settings. 

I guess the Ubuntu Sound Drivers developers need to look into latest LinuxMint(Debian Edition) audio driver.


ALL DELL 1545 Linux users try LinuxMint(Debian) you will wonder how come Intel HDA sound card is sounding so much BETTER !!!

---

### Post by FerroPower on 2011-10-07
I am attaching Alsa-Info file which I got from LinuxMint(Debian) running on my Dell 1545. Probably Ubuntu Developers need to look out whats missing because the hda intel sound just rock comparison to Ubuntu.

---

### Post by FerroPower on 2011-10-08
can any please shed some light whats the difference Alsa-info generated in ubuntu and Linuxmint Debian Differ so much ? and how come Linuxmint alsa drivers is able to use the Intel Soundcard FULLY whereas in ubuntu the sound output quality is no where near it.

---

