---
title: "No Sound on Toshiba Satellite L30 PSL30L"
date: 2009-09-13
forum: Hardware
---

### Post by mandarpalshikar on 2009-09-13
Hi All,

   I am planning to shift to Ubuntu from WIndows XP. So before doing this transition yesterday I installed Ubuntu 9.04 on my old laptop Toshiba L30 PSL30L. All the things are working very well. But I am having pronlem with sound. There is absolutely no sound being played through my laptop speakers or headphone jack. 
  lspci | grep Audio returns

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

   ALso the VOlume Control dialog box display following under Device

HDA ATI SB (Alsa Mixer)

Realtek ALC861 (OSS Mixer)

Playback: HDA ATI SB - ALC861 Analog (PulseAUdio Mixer)

  I tried tweaking with them but nothing seems to work.

AFter  following steps mentioned in [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html), now ALSA is totally gone from Volume COntrol Dialog box.

Please suggest some solution

Regards,
Mandar
[EMAIL="mandarpalshikar@gmail.com"]mandarpalshikar@gmail.com[/EMAIL]

---

