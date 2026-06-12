---
title: "Intel 865G Graphics Driver"
date: 2010-07-20
forum: Hardware
---

### Post by nitram3x3 on 2010-07-20
Hi! I'm completely new with Linux! I have recently install xubuntu 10.04 on a PC with Intel 865G Chipset and P4 CPU. The system has identified the 865G Chipset but identified the graphics drivers as ATI Rage 128 Pro Ultra instead of 865G Integrated Graphics. I believe due to this issue, the computer is extremely slow. Please Help :(

---

### Post by cascade9 on 2010-07-20
Could it be you have a ATI Rage video card installed? 

Try posting the output from 'sudo lshw' (in 'code' brackets thanks).

---

### Post by nitram3x3 on 2010-07-20
Thanks, it shown that a ATI card is present, do I need a driver for it and how?

---

### Post by cascade9 on 2010-07-20
The only drivers avaible for the ATI Rage cards is the open source driver. It should be installed by default.

---

### Post by nitram3x3 on 2010-07-20
How can I check if it has installed by default or not? The screen resolution is limited to 800 x 600 at the moment and rendering of GUI is extremely slow.

---

### Post by cascade9 on 2010-07-20
I'm not suprised its slow, its a circa 1999 video card. 

The package that supports the ATI Rage 128 (and various other cards) is xserver-xorg-video-ati. I'm not 100% sure on how you would get higher resolutions from the old Rage 128....probably creating and editing xorg.conf would be the way.

---

### Post by nitram3x3 on 2010-07-20
Thank you very much for your help, I'll have a go when I get back to my office tomorrow!

---

### Post by cascade9 on 2010-07-20
No problem, good luck ;)

---

