---
title: "[SOLVED] Widescreen Resolution No Longer Available"
date: 2008-04-23
forum: Hardware
---

### Post by 42Wired on 2008-04-23
I was trying to give a presentation in class via a VGA projector. I plugged it into my computer, and Ubuntu didn't appear to recognize it. So I booted in Vista (big mistake), which did not recognize it properly.

Since I plugged that in, in both OSs, I was stuck in 640x480. After a reboot and some playing around, Vista is fine.

I played around with the monitor driver in Gutsy and got a 1024x768 resolution, but I want to know how I can get back 1280x800.

I'm using an HP dv2000, Intel Core 2 Duo, 4GB RAM, and the dreaded Intel 965 video card.

---

### Post by nathansoz on 2008-04-23
I think that there is a resolution adjust in System-->Preferences

---

### Post by 42Wired on 2008-04-23
There isn't an option for it there. My only options are 1024x768, 800x600, and 640x480.

---

### Post by nathansoz on 2008-04-23
try running 

sudo dpkg-reconfigure xserver-xorg

in a termanal and make sure to check the resolution you want when going through the setup. This reonfigures your X server graphics and is pretty easy to run through.

---

### Post by 42Wired on 2008-04-23
I did, and when I got to the screen where I select what resolution I want, 1280x800 is the only one selected by default. After it completed, I logged out and back in, and nothing is different.

---

### Post by 42Wired on 2008-05-19
I ran it again, and now I get 1200 x 800.

---

