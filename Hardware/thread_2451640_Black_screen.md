---
title: "Black screen"
date: 2020-10-08
forum: Hardware
---

### Post by ceco26062 on 2020-10-08
Hello,:confused:


I am Tsvetan from Plovdiv, Bulgaria. I have the following problem I bought my ASROCK RX 560 Phantom 2G video card and after reinstalling the Ubuntu gnome for about 5 seconds the desktop appears and then the screen turns black and the monitor turns off. The components of my computer are: 


[LIST=1]
[*]ASROCK H310CM-HDV
[*]Intel G5420 3.8 GHz 4MB
[*]16 GB DDR 4 RAM
[*]ASROCK RX 560 Phantom 2G
[/LIST]


All settings are made correctly and correctly on the motherboard. Until 5 days ago, Ubuntu worked perfectly with the built-in video card in the processor. Please help and help me use my favorite Linux distribution again. I will wait for an answer and thank you in advance for the support.


Greetings!:P

---

### Post by TheFu on 2020-10-08
Have you looked at the log files?  The /var/log/Xorg.0.log would be good to check out.  Based on what you see inside there, you may want to see about forcing the GPU that isn't being used to be used.  At least I think the Intel G5420 has an iGPU.  My G3258 has one which works great for simple needs.

That would get you working so more research can be performed.

I think there are threads here about dual GPU setups. None of my systems have that, so I've not had to learn about it or do any troubleshooting. Google found this: [https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04](https://askubuntu.com/questions/1068343/switch-between-intel-amd-gpu-on-18-04)
[http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/04/switch-intel-nvidia-graphics-ubuntu-16-04/) is for 16.04, so it may not be applicable anymore.

What release does the system run? GUI answers almost always are release specific.

---

### Post by ceco26062 on 2020-10-08
Hello,


Thanks for the reply. The old video card was Nvidia 630 and I used a processor with built-in video and I didn't have to switch between video cards, but in this case I will have to switch for sure. I will continue to drive the case crazy and count on it if you have advice to share.


Greetings!

---

### Post by ceco26062 on 2020-10-08
To share I tried to install Ubuntu 18.04.05 and there are no problems with the video card, it is recognized as Radeon RX 460 and does not cause problems, but at the moment I give an upgrade after the restart with the new 20.04 and the screen turns black. I wonder what this is due to. Thanks in advance for the advice and answers.


Greetings!

---

