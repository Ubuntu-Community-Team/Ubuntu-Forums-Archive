---
title: "Info about bumblebee on Gaming Laptop"
date: 2015-11-21
forum: Hardware
---

### Post by blade4 on 2015-11-21
Hey all , 

I recently installed wiley on my MSI GT70-0NC laptop ( core i7 version ) and am debating on whether or not I should install bumblebee. I do intend to go for some casual gaming ( to not game would be an insult to the hardware ) . So I wanna know if anyone has done the deed on a similar setup and if so , what was your experience and what should I be on the lookout for . Spec details as follows : 

Processor : Core i7-3610QM 
RAM : 16 GB 
GFX : NVIDIA Geforce GTX 670M with Optimus ( 3GB VRAM ) 

Any opinions /tips /warnings would be welcome :) 

Cheers !

---

### Post by efflandt on 2015-11-21
For the laptop in my sig, I have not used bumblebee since Ubuntu 13.10 before nvidia-prime was available in Linux. At that time *optirun* worked, but needed extra parameters to launch steam Source games. I could not get *primusrun* to work for anything at all.

From Ubuntu 14.04 on, if you install nvidia drivers they include nvidia-prime and hybrid graphics can be switched between Intel and Nvidia using *Nvidia X Server Settings*. After switching Nvidia to Intel I just have to log out of X and back in, but going Intel to Nvidia I need to reboot (or it goes to low graphics mode). Maybe not on the fly, but both the Intel and Nvidia graphics seem to work better without needing any extra parameters for games like optirun from bumblebee required.

---

### Post by blade4 on 2015-11-23
> [COLOR=#000000]For the laptop in my sig, I have not used bumblebee since Ubuntu 13.10 before nvidia-prime was available in Linux. At that time [/COLOR]*optirun worked, but needed extra parameters to launch steam Source games. I could not get [I]primusrun to work for anything at all.*[/I]

Thanks for the tip efflandt. I tried installing the proprietary NVidia drivers but on rebooting I noticed that I'm getting graphical artifacts on the screen - especially when I resize windows. I guess I'll be using Noveau drivers for a while longer then.

---

