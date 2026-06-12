---
title: "HDMI sound"
date: 2011-11-13
forum: Hardware
---

### Post by smidge on 2011-11-13
I have not been able to get sound through my intel hdmi port
I found a link

[http://lists.freedesktop.org/archives/xorg/2008-November/040034.html](http://lists.freedesktop.org/archives/xorg/2008-November/040034.html) 

to patch sound through HDMI on intel chipsets but i have no idea how to patch this. anyone got a clue?

ps. also cant get the hdmi screen to work by itself connected to my laptop, although it works fine if i use it as a secondary monitor.

---

### Post by MoreOrLess on 2011-11-13
You're making it too difficullt. The patch was applied to upstream ALSA years ago. All you should have to do is set your apps (or pulseaudio) to output to the HDMI device..

---

### Post by smidge on 2011-11-13
thats the whole issue, audio playback isnt working though hdmi even though the audio channel is supported. could you tell me how to set it manually? maybe i missed something.

---

