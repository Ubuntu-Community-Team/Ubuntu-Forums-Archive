---
title: "Sound problems on Acer Aspire 5002WLMi"
date: 2009-03-31
forum: Hardware
---

### Post by mraza on 2009-03-31
Hi,

I just installed Ubuntu 8.10 on my laptop and I have noticed that the sound is not working properly. I can hear the startup/logon sounds just fine. And sometimes I get the sound from youtube videos too, but on skype the sound wasn't working at all, so I went into the options and fiddled with sound source, it listed 4, I went through all of them I found that the best it can do is give me audio in left channel only.

My sound card used to work fine before, I have installed Ubuntu 6/7 on this laptop before, everything worked perfectly straight out of the box (I had to install drivers for the WiFi card, but Ubuntu found the drivers and all I had to do was click "install", just like this time). My sound has worked fine in previous installs of Ubuntu.

I think this is causing my web browsers to freeze as well, Firefox was freezing when I clicked on a particular URL, unless I open it in new tab, I tried re-installing Firefox, but that didn't help. Then I installed Opera, and it froze at the same point. I read on the web that adding "alsa-oss" somewhere in firefoxrc can fix this, but I can't find firefoxrc on my installation.

When I do 
```
aplay -l
```
this is what I get
```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


-M Raza

---

