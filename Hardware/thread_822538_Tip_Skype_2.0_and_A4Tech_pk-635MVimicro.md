---
title: "Tip: Skype 2.0 and A4Tech pk-635M/Vimicro"
date: 2008-06-08
forum: Hardware
---

### Post by fhmanas on 2008-06-08
Hello, for those having problems with this config or using similar vimicro device, i found this link to be the one that solved my problem.

[http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html](http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html)

Basically, the device 'zc0301' is giving problems and the tip involves disabling it. 

sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe gspca

shows also how to make permanent by editing /etc/modprobe.d/blacklist and adding 

blacklist zc0301

This tip worked like a charm, and video was working in skype.  Thanks, UbuntuGeek!

Left this for people having similar problems

---

