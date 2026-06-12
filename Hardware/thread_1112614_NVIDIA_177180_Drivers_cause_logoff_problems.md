---
title: "NVIDIA 177/180 Drivers cause logoff problems"
date: 2009-03-31
forum: Hardware
---

### Post by AeroNautica0909 on 2009-03-31
Hey all!

I'm having a problem on my Thinkpad T61p laptop. First, I have a NVIDIA Quadro FX570M graphics card.

I am currently using the NVIDIA 173 drivers on Ubuntu Intrepid. The 173 drivers, when you log off, does not give any problems or any waiting time. The 177/180 drivers has a logoff lag time problem which can be fixed in the gdm.conf file.

Interestingly enough, I have GdmXServerTimeout set to 60 when I installed the NVIDIA 180 drivers. However, when I log off, the screen goes black, I see the mouse as if it is about to go to the login screen, then it goes black again. This continues until I get an error. For some reason, I'm having the same problem with the 177 drivers as well.

Would anyone know how to fix this? I already set my GdmXServerTimeout as I've found at the Thinkpad T61p Wiki for Ubuntu 8.10. Do I need to set it higher than 60 seconds or is there some other problem? Any help is greatly appreciated!

---

