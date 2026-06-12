---
title: "How To Get Wacom Intuous 5 Pen and Touch Working in 16.10"
date: 2017-01-02
forum: Hardware
---

### Post by linux4me on 2017-01-02
I was happily using Ubuntu 14.04, and had every expectation of continuing to do so until it was no longer supported; however, I got a new Wacom Intuos 5 Pen and Touch Drawing Tablet for work, and everything changed. I did some research before hand--evidently not enough--and thought it would work out-of-the-box with Ubuntu 14.04. That was not the case. Although it was recognized by lsusb, Settings -> Wacom Tablet did not recognize it, and if I enabled the stylus in GIMP, it didn't work. There is apparently a conflict between unity-control-panel and the Wacom tablets that do not have a stylus on the eraser. According to a bug report I saw, the issue was resolved in gnome-control-panel version 3.20, which I saw was available in Ubuntu Gnome 16.10. 

I did a clean install of Ubuntu Gnome 16.10, but the tablet still wasn't recognized in the Wacom Tablet Settings, and wouldn't work in GIMP. The tablet was listed in lsusb.

I ended up getting it working by installing xserver-xorg-input-wacom:
```
sudo apt install xserver-xorg-input-wacom
```
and then restarting.

My tablet is now recognized in Settings -> Wacom Tablet, and I was able to configure the buttons. The buttons and stylus work fine in GIMP.

---

