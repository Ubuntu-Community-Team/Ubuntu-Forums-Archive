---
title: "Nvidia drivers."
date: 2009-06-02
forum: Hardware
---

### Post by djaggar on 2009-06-02
I understand its a very common problem to have display issues when first installing Ubuntu. I have visited coutless forums telling me dozens of different ways to get nvidia drivers working and I'm still experiencing the same problems. 
 
1st. On ever boot and even on the install there was a message about being unable to detect display :0 and using display :1 instead. I get this message every time I boot.
 
2nd. Once I install the Nvidia drivers (no matter which method I use) I try and access 
the settings and get presented with this message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." Ok so I sudo nvidia-xconfig, and log-off to resart the x server. Still presented with the same message. 
 
3rd. Once I have the drivers installed (although obviously not working) upon reboot I am presented with one of these messages:
 
(EE)NVIDIA(0): Failed to load nvidia kernel modual!
(EE)NVIDIA(0): ***ABORTING***
(EE)Screen(s) found but none have usable configuration
 
or something along the lines of:
 
(EE)NV(0): Failed to detect available video memory
 
Any help would be greatly apreciated. Thanks for your time.

---

### Post by David Crockett on 2009-06-03
I have the same issues with my old Dell and TNT series video card.   Although I do not see the error messages that you see on boot (or alt least I have not noticed them).   I tried the sudo nvidia-xconfig command line and all I get is bad command.

It is a bummer to say the least.

---

