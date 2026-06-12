---
title: "Monitor stuck in low resolution"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by rpworth on 2008-03-28
I am a new Kubuntu user starting today and was hoping it work just "work" which is what I'd heard about Ubuntu installations from other beginners who've tried. But I do not seem able to get my monitor out of very low resolution graphics (800 x 600) when I previously used 1280 x 800 on my windows installation.

My specs:
Vaio notebook (VGN-BX660P49)
ATI Mobility Radeon X1600 (128 MB), resolution previously set to 1280 x 800
When I started Kubuntu for the first time, it offered me to use "restricted drivers," so I did that. In the control panel it says the driver is fglrx. I also installed the ATI control panel from the package manager, but it does not allow you to change the resolution.

When I go to the control panel and attempt to change the resolution, the highest resolution I can move the slider to 800 x 600. What should I do?

Any advice is appreciated. If you need more information, let me know.

---

### Post by housam on 2008-03-28
type in the terminal```
sudo dpkg-reconfigure xserver-xorg
```
and leave every thing as it is except the resolution you want to change.

---

### Post by rpworth on 2008-03-29
That worked. Thanks!

---

### Post by noctiphile on 2008-04-02
> **housam said:**
> type in the terminal```
sudo dpkg-reconfigure xserver-xorg
```
and leave every thing as it is except the resolution you want to change.

I recently had to run that command and found it's easier to use the -p option as follows:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This way asks only about the resolutions so you don't have to figure out how the mouse and keyboard are supposed to be set up.  If you forget what the command is, it's stated in the header of /etc/X11/xorg.conf.

---

