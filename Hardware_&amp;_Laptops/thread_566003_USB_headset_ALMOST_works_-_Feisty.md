---
title: "USB headset ALMOST works - Feisty"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by redliner777 on 2007-10-02
Hi,

I'm fairly new to Linux, but I've been doing a lot of research and getting everything setup. I have almost everything configured so that I have all the functionality of the mainstream OS. However I have a small problem with my usb headset. 

For playback I can select USB or dmix:0 in any of my applications and it will work. Recording/capture however not so much. The only option I have for recording is dsnoop:0. I have gon in all the mixers and made sure the mic was enabled, I can hear myself speak in it. and on soundrecorder I can record my voice and play it back.

I have tried creating ~/asound.rc, as well as /etc/asound.conf If either of these are enabled the system acts like OSS in that only one application can have the card at a time and my mic still doesn't work. So obviously I run without them at all since that gives me the closest thing to correct functionality.

I should point out that the specific area of my problem is in anything I run under wine. Both ventrilo and wow (now has voice chat) show choices of dmix:0 and usb for playback but only dsnoop:0 for capture. 

I tried running wine with oss and everything works great, I see both cards for both playback and capture. So when I try running aoss <application> it's great, I get sound from multiple applications, but my mic won't work.

I have been working on this for days, if I left anything out, or rambled too much I'm sorry. I'm just tired and frustrated.

Thanks,
Brian

---

