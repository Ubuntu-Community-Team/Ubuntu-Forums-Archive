---
title: "NVIDIA GeForce GT 630M driver issues 12.04"
date: 2012-09-09
forum: Hardware
---

### Post by JECHO on 2012-09-09
Hey guys I just got a new Dell XPS 14 ultrabook and installed ubuntu 12.04 x64 on it. 

I've already installed bumblebee and the bumblebee-NVIDIA package via the repo but I'm hoping there is a better way to make use of the GPU than having to specify each time I want to use it. 

Ideally I'd like the Dessktop environment to utilize the graphics card so the visual effects are more fluent. As of now the general OS and DE are just using the integrated graphics and to be honest it kind of sucks. 

I tried also installing the NVIDIA-current package to hopefully get it working that way and haven't had much luck. After a reboot I tried running the NVIDIA settings GUI and got a message that there was no xorg.config in use and I needed to create one so I did. After a reboot, the highest resolution I could get was crap. So obviously that didn't work :(


Any help with how to get this card working properly would be appreciated!

---

### Post by typhoon_tip on 2012-09-09
Unless there is a setting in the BIOS to switch off the integrated graphics and use only discrete, you are stuck with Bumblebee. Have a look at it and report back.

---

### Post by JECHO on 2012-09-09
> **typhoon_tip said:**
> Unless there is a setting in the BIOS to switch off the integrated graphics and use only discrete, you are stuck with Bumblebee. Have a look at it and report back.

No setting in the BIOS to force the use of nvidia :(

I refuse to believe that I'm "stuck" - surely somebody else has had this issue with this video card (I hope) :(

I dont mind being stuck with bumblebee but if so, do you happen to know if there is a way to force lightdm to use nvidia?

---

### Post by typhoon_tip on 2012-09-11
Even if there's a way to run entire GUI over NVIDIA, you would not get any good advantages, and it would be terribly complicated and risky to do. You cannot shutdown integrated card with Optimus technology. The display is connected to the integrated card only, as there is no MUX. Thus, shutting down the integrated graphics basically shut down the display, unless the BIOS manage this you can use only Bumblebee.

On a personal note, this is one reason I stick with ThinkPad laptops only. You pay more, but you also get a hell of a lot more imo. BIOS settings allow you to do all kind of combinations that you want (hybrid, discrete only, mixed mode, integrated...).

I was reading a thread on linuxforums that suggest to flash another bios... but this is more risky than setting up the GUI to run with "optirun" !

---

### Post by JECHO on 2012-11-01
> **typhoon_tip said:**
> Even if there's a way to run entire GUI over NVIDIA, you would not get any good advantages, and it would be terribly complicated and risky to do. You cannot shutdown integrated card with Optimus technology. The display is connected to the integrated card only, as there is no MUX. Thus, shutting down the integrated graphics basically shut down the display, unless the BIOS manage this you can use only Bumblebee.

On a personal note, this is one reason I stick with ThinkPad laptops only. You pay more, but you also get a hell of a lot more imo. BIOS settings allow you to do all kind of combinations that you want (hybrid, discrete only, mixed mode, integrated...).

I was reading a thread on linuxforums that suggest to flash another bios... but this is more risky than setting up the GUI to run with "optirun" !


Agreed but the Lenovos design is lacking... a lot.

---

### Post by typhoon_tip on 2012-11-02
> **JECHO said:**
> Agreed but the Lenovos design is lacking... a lot.

Totally agree. Is a laptop designed for hard, reliable operation, not really designed to be fashionable !

---

### Post by dzoniub on 2012-11-20
Hi, i have recently installed Ubuntu 12.10, and I have the same problem. I have tried bumblebee, but no help...I have also tried to type in terminal sudo apt-get purge nvidia-current, but then when i restart my laptop i get only desktop but without icons and i can't do anything...Had to reinstall Ubuntu...My laptop is acer 5750g, graphics nvidia 630m...When i go to system settings/details/graphics it says driver is unknown...Any solutions?

---

