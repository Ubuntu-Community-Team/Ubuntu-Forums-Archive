---
title: "Creative Sound Blaster X-Fi Xtreme Audio CA0106 Drivers"
date: 2017-12-29
forum: Hardware
---

### Post by philip10 on 2017-12-29
How do I reinstall audio drivers? specifically snd-ca0106

aplay -l
aplay: device_list:268: no soundcards found...

sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

lspci | grep -i Audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
03:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

Ubuntu 16.04

---

### Post by philip10 on 2018-05-18
[https://askubuntu.com/questions/990915/creative-sound-blaster-x-fi-xtreme-audio-ca0106-drivers/1037728#1037728](https://askubuntu.com/questions/990915/creative-sound-blaster-x-fi-xtreme-audio-ca0106-drivers/1037728#1037728)

---

