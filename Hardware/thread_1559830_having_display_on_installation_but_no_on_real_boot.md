---
title: "having display on installation but no on real boot from hd"
date: 2010-08-24
forum: Hardware
---

### Post by baosheng on 2010-08-24
I am having a strange problem that Ubuntu can work with my graphic card and monitor during installation, but has no display signal since the first boot from hard drive. 

I have an HP Z400 6-DIMM workstation using Nvidia Quadro NVS 295 graphic adapter. The graphic adapter has dual HDMI output ports. I connected an HDMI-to-DVI adapter with one port and used an DVI cable to connect to the monitor. 

In installation or try-from-live-cd, the display had no problem. Everything worked fine. But, the monitor showed nothing since the first "real" boot from hard drive. The monitor went into power saving model after grub. I can hear the don-don sound of Ubuntu login screen later. But still nothing. 

I tried to switch to command line model using Alt+Ctrl+F1. But nothing on the screen either. 

Can some one help me?

---

### Post by Palecomic on 2010-09-24
I have the same problem and also have an HP z400 and NVIDIA Quadro NVS 295 graphics card.  It's very frustrating, did you manage to find a solution?

Thanks for your help

---

### Post by Palecomic on 2010-09-27
For reference I've fixed this in case someone has the same issue.

Though it wasn't possible to enter recovery mode or boot from command line, Ubuntu had installed correctly so I was able to login remotely via SSH, then did the standard:

sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot

and it sorted the problem immediately.

---

