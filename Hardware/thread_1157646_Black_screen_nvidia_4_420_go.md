---
title: "Black screen nvidia 4 420 go"
date: 2009-05-12
forum: Hardware
---

### Post by sbdd on 2009-05-12
Hi! I have one problem.  After installing nvidia propriatic drivers after reboot i got sound of log in, but black screen. 
What i have tried to do:
1) Install drivers from official site. (closing x-windows). Result - the same
2) Install drivers using EnvyNG. Result - I have normal working drivers, but i have only 800x600 screen resolution and a black line on the right on the screen.
Notebook Toshiba Satellite (old); p4, 256 RAM, Nvidia 4 420 go,40GB hard disk. Help plz ](*,)

---

### Post by overdrank on 2009-05-12
> **sbdd said:**
> Hi! I have one problem.  After installing nvidia propriatic drivers after reboot i got sound of log in, but black screen. 
What i have tried to do:
1) Install drivers from official site. (closing x-windows). Result - the same
2) Install drivers using EnvyNG. Result - I have normal working drivers, but i have only 800x600 screen resolution and a black line on the right on the screen.
Notebook Toshiba Satellite (old); p4, 256 RAM, Nvidia 4 420 go,40GB hard disk. Help plz ](*,)

Hi and welcome, When you have the working driver and limited resolution, have you tried adjusting the resolution with nvidia-settings?
Using the alt, F2 keys and enter the command ```
gksu nvidia-settings
```
Also with the graphics sharing the limited memory of 256mb this may cause some issues also.

---

### Post by sbdd on 2009-05-12
have you tried adjusting the resolution with nvidia-settings?

I v tried it using Nvidia  xserver utility that installed with driver. There i had only 800x600 or lower.

---

### Post by overdrank on 2009-05-13
> **sbdd said:**
> have you tried adjusting the resolution with nvidia-settings?

I v tried it using Nvidia  xserver utility that installed with driver. There i had only 800x600 or lower.

Sorry for the delayed response. What version of Ubuntu are you using? Could you please post the output of this command ```
cat /etc/X11/xorg.conf
```

---

