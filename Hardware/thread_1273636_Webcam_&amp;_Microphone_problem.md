---
title: "Webcam &amp; Microphone problem"
date: 2009-09-23
forum: Hardware
---

### Post by Saucisse on 2009-09-23
Hi guys,
I am pretty new in the Linux world and I have some difficulties doing basic stuff. Okay yesterday I got to install Skype thanks to the forum, and today I am stuck with the webcam and sound installation.
When I plug in my webcam, there is the green light on the webcam on as if I was constantly using it. But when I am making a call on Skype, there is no webcam and no microphone. It doesnt recognize it actually. Maybe bcause its a Microsoft ? :)
Its a LifeCam VX-1000.
Also, I have a laptop and there is an integrated microphone but Linux doesnt seem to recognize it either. Thanks very much for your time and help.
:KS

---

### Post by Saucisse on 2009-09-23
Pleasse... Help me !

---

### Post by ajemig on 2009-09-26
I'm terrible with computers and new to linux (not a good combination).
I'm having a similar problem.  I cannot get my microphone to work, either the one built in with my camera (VX3000 I believe), or the mic from a headset I have.

Have you tried testing your video cam in the Skype Menu? (Options > Video Devices)  Is the right type of advice entered?

Does anybody have any advice for the microphone issue?

Thanks

---

### Post by stanca on 2009-10-07
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r) ;)

---

