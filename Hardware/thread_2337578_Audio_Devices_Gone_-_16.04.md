---
title: "Audio Devices Gone - 16.04"
date: 2016-09-19
forum: Hardware
---

### Post by tvrdoglavi on 2016-09-19
I was trying to get Guitarix work and experimented a bunch with Jack. After a reboot, all my audio devices are gone. They are not listed anywhere.
I have a USB Audio Interface Edirol UA-25EA and USB Headphones connected. There is also an HDMI soudcard from the graphics card.
All of them work fine on my Windows and OpenSuse installs. I'm pretty new to Linux and have no idea where to start troubleshooting this. Any pointers would be appreciated.

---

### Post by Yellow Pasque on 2016-09-20
Most likely, JACK started and blocked pulseaudio. Stop JACK and start pulseaudio. If you need more detail, then you should give more detail on exactly how you setup JACK.

---

### Post by tvrdoglavi on 2016-09-21
Thank you for the post. I not only stopped jack, but I removed it from the system and it still didn't help. I ended up reinstalling last night.

---

