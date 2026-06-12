---
title: "Input device--USB SNES controller--won't register two of the direction buttons"
date: 2013-04-28
forum: Hardware
---

### Post by jplaj on 2013-04-28
I'm trying to set up retro gaming emulators using a USB to SNES controller adaptor. I bought a hardware piece (in some places called "Super Smart Joy" and elsewhere referred to "GTron SNES to USB Converter." The device promises plug and play, and works very well on my old Windows Vista system. Just stick it in the slot, and all my emulators detect the input for all the buttons and axes. 

However, in Linux, it doesn't exactly work right. Same deal as Windows--plug and play and the computer and emulators recognize that it's there. Most of the buttons work perfectly fine, and I can set them as inputs for the games, but the Right directional pad and the Down directional pad don't register anywhere.

I've tried various joystick calibration packages (and made sure, as per other forum posts, that I uninstalled them so they don't interfere with each other), and the only thing I accomplished was being able to use my PS3 controller as a mouse. I've also tried multiple SNES controllers (including an off-brand), all with exactly the same results. 

Does anyone know how I may be able to fix this problem and get Ubuntu to read those other two buttons, OR can anyone point me in the direction of a controller or adapter that will work well with Linux and various emulators for 8- and 16- bit gaming systems? (Preferably inexpensive, but functional options)

I'm working on Ubuntu 13.04, but eventually hoping to reproduce my setup on a Raspberry Pi. I've been using Ubuntu for a few months, and I know my way around, but I may need to be walked through anything more complicated than typing commands into terminal. 

Thanks.

---

### Post by davidbaumann on 2013-04-29
Firstly, please show the result of lsusb.

---

### Post by jplaj on 2013-05-17
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b336 Chicony Electronics Co., Ltd
Bus 002 Device 003: ID 0925:8866 Lakeview Research WiseGroup Ltd, MP-8866 Dual Joypad

(Sorry for the delayed response, but thank you for the help)

---

### Post by MoreDistortion on 2013-09-27
I have the exact same problem, the down and right directions on the d-pad do not register at all. All other buttons and up/left d-pad directions are working. lsusb shows my dual joypad and I can see the controller from jstest-gtk. So far calibration has had no (positive) effect.

---

### Post by Yellow Pasque on 2013-09-28
I have to run these two commands to get a Logitech joystick d-pad working properly (after I plug it in):
```
sudo setfacl -b /dev/input/event*
sudo chmod 640 /dev/input/event*
```

---

### Post by Hangman228 on 2014-08-28
Here is a bug report : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362643](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1362643)
Sorry for the delay...

---

