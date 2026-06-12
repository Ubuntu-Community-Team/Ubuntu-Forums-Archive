---
title: "Microphone input not registering."
date: 2010-04-18
forum: Hardware
---

### Post by TheCommissar on 2010-04-18
Sound recorder/skype etc does not recognise any sound coming from the mic I have plugged in.

I have 9.10 installed on a Dell Inspiron 1545. Any suggestions would be great.

Many thanks.

---

### Post by khelben1979 on 2010-04-18
[Pulse audio]("http://en.wikipedia.org/wiki/Pulse_audio") have been the solution for this, for some. So read on about it if you don't go to the second solution:

Otherwise, another solution is to connect a USB headset and tell Skype to use this as sound input in the Skype settings.

---

### Post by lidex on 2010-04-18
Are you familiar with alsamixer? In a terminal="Applications>Accessories>Terminal"
```
alsamixer
```
Press F4 for capture devices. Scroll L/R with L/R arrow keys. Change values with Up/Dn arrow keys. Input sources with no graphic can be toggled line/mic.

---

### Post by lidex on 2010-04-19
Section "Skype" here:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

---

### Post by TheCommissar on 2010-04-19
I ended up buying a USB headset in the end, thanks for the info on pulseaudio though, I didn't have the volume control installed, I think. Thanks for your help.

---

