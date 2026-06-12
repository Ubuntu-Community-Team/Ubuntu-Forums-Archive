---
title: "Display resolution is stuck at 1024x768 and hot keys are not working for brightness."
date: 2014-09-13
forum: Hardware
---

### Post by mohi2 on 2014-09-13
I'm having problem with my display resolution in Ubuntu. My laptop supports 1366x768 resolution and it was set at it as well. 
But today all of a sudden my system hanged and when I restarted it through power button, it's stuck at 1024*768. I checked 
**System Settings>Displays **but there's only 1024x768 (4:3) and 800x600 (4:3) option available.


By the way I've two graphic cards in my system, Intel and Nvidia. I tried to install Nvidia driver yesterday but there was this black screen problem so I purge removed it through recovery console mode. After that my system has again start using the Nouveau display driver. 


Additional problems which has started with the resolution problem are:


[LIST]
[*]Hot keys to control brightness has stopped responding, resulting in brightness stuck at maximum as well.
[*]After suspending or logging out can't go back to login screen, because screen remains off , although machine starts which I can check through LED lights. So I always have to use power button to get access to the screen again.
[/LIST]


I thought my Intel display driver got broken or uninstalled so I re-installed it with this:


**$ sudo apt-get install xserver-xorg-video-intel**


then reconfigured x server with this and rebooted:


**$ sudo dpkg-reconfigure xserver-xorgre**


But it didn't solve my problem. 


Can anyone please identify the actual problem and help fixing it. I'm a linux newbie. I've alraedy installed to many software etc. in my Ubuntu machine that I can't afford to re-install it just beacause of this problem.

---

