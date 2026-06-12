---
title: "Sound goes to mute, strange issue..."
date: 2014-02-18
forum: Hardware
---

### Post by Huruk on 2014-02-18
Hi all, this is my first post on that forum, I was using ubuntu few years ago and never handled something to strange...

All this problem starts when I detected that my laptop (toshiba satellite 750) loses sound randomly when its reproducing something. I mean, playing music, watching film, skype conference, etc...

The strange thing is that all this problem I was experimenting in windows 7 before. I have migrated to ubuntu 12.04 hopping it was my salvation but, at first 10 minutes of use I got a facepalm and my speakers become muted too.

Maybe its a driver problem or hardware, could you help me to identify where is the problem and latter we will try to fix it ;)

Thanks in advance.

---

### Post by Huruk on 2014-02-20
Hi, I have more information...
 - When the sound goes, sudo killall pulseaudio bring it back, but some minutes later it dissapeare again.
 - I found a thread on Toshiba forums where explains something about rebaling a pin conexion, the problem is that I cant find this conexion on my model. [http://forums.toshiba.com/t5/Audio-Sound/no-sound-usb-on-satellite-l505d-gs6000/m-p/343546#M10329](http://forums.toshiba.com/t5/Audio-Sound/no-sound-usb-on-satellite-l505d-gs6000/m-p/343546#M10329)

Any ideas?

---

### Post by Huruk on 2014-02-25
Edit

---

### Post by tgalati4 on 2014-02-25
Sound chips get hot and over time some can delaminate (lift off the motherboard).  By rebooting or killing pulseaudio, the chip cools down and makes contact.  It heats up playing sound for a few minutes then lifts off of the board which breaks the connection.  With your machine apart and running, put your finger on the sound chip and press down.  If the sound returns then you know you have found the problem.  Repair is not easy nor is it successful.  You need to reflow the solder connections under a tiny chip.  At this point, buy an external USB sound dongle and use that.  The risk of destroying the motherboard trying to reflow a single chip is high--unless you know what you are doing.

---

