---
title: "Microphone not working on Ubuntu 16.04 (Intel NUC5i5MYBE)"
date: 2018-02-20
forum: Hardware
---

### Post by kad-m on 2018-02-20
Hi experts,
 

On  an Intel NUC5i5MYBE board running Ubuntu 16.04 OS, I want to run voice  recording and playback applications (with ALSA module). I use a standard  headset connected to the front panel jack port.

 
On  Windows 10, I have installed the Realtek High Definition Audio Driver  delivered by Intel.  After that, the headset (microphone and headphone)  work fine. This means the issue is not due to hardware mismatch between  the headset and the jack port.
 
On  Ubuntu 16.04 and Ubuntu 17.05, only aplay works as expected. The  microphone doesn't seem to be detected. Although it appears as Built-In  Audio in PulseAudio, changing the input volume doesn't affect the input  level, always 0. The sound card is visible in /proc/asound/card1 and  uses the Codec ALC283. Alsamixer shows 'Mic Boost', 'Capture' devices.  When devices are set to 100% volume and 'Capture' is set as recording,  arecord only gets null packets.

I followed the steps explained in [HdaIntelSoundHowto - Community Help Wiki]("https://communities.intel.com/external-link.jspa?url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FHdaIntelSoundHowto"), section 'Extra Hints to Get Sound Working' without success. Adding the line 'options snd-hda-intel model=auto' to /etc/modprobe.d/alsa-base.conf didn't solve the problem.

 

Are there a specific ALSA configuration to set for the ALC283 module or a driver installation for Ubuntu that I missed?

 
Thanks.

---

