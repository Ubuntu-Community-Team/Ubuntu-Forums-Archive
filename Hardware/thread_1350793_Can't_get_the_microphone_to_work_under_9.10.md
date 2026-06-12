---
title: "Can't get the microphone to work under 9.10"
date: 2009-12-09
forum: Hardware
---

### Post by TCarlsen on 2009-12-09
Hey

Ubuntu 9.10
Hp Pavilion tx1000
Realtek ALC861-VD

Have Gnome ALSA Mixer installed and unmuted "Capture" and "ATAPI Mic" and turned them up.

The sound on the system is no problem, only the inbuild mic.

Hope someone can help me :)

---

### Post by Favux on 2009-12-12
Hi TCarlsen,

Don't have a TX1000 so I don't know if this will work.  Some thoughts anyway.

In alsasmixer change Input Source to Front Mic.  (You may need to go into alsamixer in a terminal. Once you are in there, press the right arrow until you see Input Source. If you don't see that entry, press tab until you do. Make sure that it is set to Front Mic.) Use the volume control in the system tray to set Front Mic and the Front Mic Boost as high as needed. Play around with the Capture and Digital controls until your voice is clear. Fan noise or the display buzz may get into the sound, but you should be able to get voice reasonably clear. Try Capture volume at around 65 and Digital at 40.

Hope this is helpful.

---

### Post by TCarlsen on 2009-12-14
It's all set like you say.. but still no record sound :(

---

