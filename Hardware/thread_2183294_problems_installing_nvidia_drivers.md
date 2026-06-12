---
title: "problems installing nvidia drivers"
date: 2013-10-24
forum: Hardware
---

### Post by mino-98 on 2013-10-24
[COLOR=#333333][FONT=UbuntuRegular]Hi, i have a laptop with Ubuntu 13.10 GNOME in it. GNOME Shell version is 3.10.1. Here's what I got from running the following command:[/FONT][/COLOR]
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor
Family Integrated Graphics Controller (rev 09)    
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce 610M] (rev a1).

```[COLOR=#333333][FONT=UbuntuRegular]In the Additional Drivers panel, I just have my wifi card driver. How can I install Nvidia drivers without using bumblebee and via ppa? I'm really confused about this. I would like to install the 319.17 drivers, which are the stable version for my graphics card. I don't know what to install (nvidia, nvidia-current, nvidia graphic 319, etc.) .Could you tell me what I have to do to install nvidia drivers?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I tried going to *System Settings* -> *Software & Updates* -> *Additional Drivers* to check for additional Nvidia drivers, but there weren't any Nvidia drivers in the list in the Additional Drivers tab. However when I checked in the Ubuntu Software Center, there were several different nvidia packages there, as shown in this screenshot: 
[http://imageshack.us/photo/my-images/22/8w0l.png/](http://imageshack.us/photo/my-images/22/8w0l.png/)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have already tried to install the nvidia-319 package from the Ubuntu Software Center, but after reboot Ubuntu did not load correctly. I could only see the mark of Ubuntu GNOME and nothing else, the desktop or GNOME Shell didn't even load. I also couldn't go to the login page. Then I removed the nvidia-319 package, and now I have my system back. Through all of this I have been using the default gdm package for the login screen display manager application.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I still don't know what Nvidia package to install and how to get the proprietary Nvidia graphics package to work on my system. Please help. 
Thanks in advance!):P[/FONT][/COLOR]

---

