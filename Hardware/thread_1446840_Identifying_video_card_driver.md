---
title: "Identifying video card driver"
date: 2010-04-04
forum: Hardware
---

### Post by happysadhu on 2010-04-04
Hi, I wanted to check to see if I've installed the RadeonHD driver for my ATI x1400 graphics card is working -- i.e., I installed it correctly. I would I go about identifying the current video card driver in use. There is nothing in my xorg.conf file to go by.

I installed the RadeonHD driver through synaptic manager (xserver-xorg-video-radeonhd). Hopefully, that's all that's required to switch from the default Ubuntu open source driver to the RadeonHD one. My Gateway monitor appears to be a little crisper, but it could just be my imagination. I was having issues with monitor blurriness before even after playing around with fonts and their settings. 

Thanks for the help, Sam

---

### Post by axelabs on 2011-02-24
The following command gives me a good idea of what Xorg is using:

```
egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log
```

If that does not help you, try the following article:
[http://stackoverflow.com/questions/4984817/how-to-check-the-information-of-current-installed-video-drivers-on-ubuntu](http://stackoverflow.com/questions/4984817/how-to-check-the-information-of-current-installed-video-drivers-on-ubuntu)

---

