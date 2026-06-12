---
title: "AMD catalyst 14.12 Omega drivers: only black screen with cursor in games"
date: 2015-03-15
forum: Hardware
---

### Post by micha2358 on 2015-03-15
The AMD graphics driver used in Ubuntu 14.10 made no problems. I upgraded to the Omega drivers which were released last december. There is a significant perfomance boot in some games, so this driver seems to be great.
 But in many other games, i have only a black screen and i see the game's mouse cursor. Ok, i switched back to the older drivers and the problem was gone.
Now I upgraded to Ubuntu 15.04 which uses the Omega drivers. So the black screen/cursor only problems are there again. Of course I don't want to downgrade to a lower driver than originally used in 15.04. And of course I finally want to use the current driver because of it's better performance.

I have a good feeling that there may be an easy fix to the problem because when i start such a game where i can only see the cursor I realised the following:
When I press the volume keys on my keyboard, I can see for only half a second the game's graphics. So the driver seems working at all! There is just a black overlay.

Any idea how to get rid of this black overlay?

---

### Post by micha2358 on 2015-03-17
At least i would like to know if other users have the same issues when using the AMD drivers from december 2014 on a Ubuntu system?
It's hard to believe that such an issue isn't fix for almost 3 month.
How will Linux ever be a gaming platform when there are no fixes for such minor issues?
I want to make clear once again: the driver seems to work, there is only a black overlay in some games, which disappears shortly when I press the volume key.
...and it only disappears once, so it doesn't do the trick to press the volume key repeatedly ;)

---

### Post by Mark Phelps on 2015-03-17
Folks might be able to help if you told us (1) what AMD video chipset you are using and (2) specifically what games exhibit the black screen.

---

### Post by micha2358 on 2015-03-18
My graphic adapter is a Radeon HD 5800 and I figured out that all games with this issure are Unity based games.
Hope that helps...

---

### Post by Mark Phelps on 2015-03-18
Was just checking to see if have one of the "legacy" AMD chipsets -- which you don't.  The Catalyst 14.12 Omega drivers should work fine with an HD5xxx chipset.

Sorry, not a Gamer so I can't help with the Gaming problem.

---

### Post by micha2358 on 2015-06-11
After just a half year of waiting, AMD finally released a new driver (version 15.5 Omega). After installation,  the desktop environment won't start anymore. All I get is the following text message on a black screen: Starting Version 219.
It surely has to do with the systemd-package and I already tried this command:

$ sudo systemctl enable sddm.service -f
$ sudo reboot

...but no success :(

Any ideas? I would be very pleased to receive any suggestions.

---

### Post by micha2358 on 2015-07-05
Here are my system details. Maybe it helps providing a solution?
```

System:    Host: michael-P5E3-Premium Kernel: 3.19.0-21-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.04 vivid
Machine:   Mobo: ASUSTeK model: P5E3 Premium v: Rev 2.xx
           Bios: American Megatrends v: 0803 date: 05/21/2009
CPU:       Quad core Intel Core2 Extreme X9770 (-MCP-)
           speed/max: 2400/3200 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cypress XT [Radeon HD 5870]
           Display Server: X.Org 1.17.1 drivers: ati,fglrx (unloaded: radeon)
           Resolution: 1680x1050@59.9hz
           GLX Renderer: AMD Radeon HD 5800 Series
           GLX Version: 4.4.12874 - CPC 15.20.1013
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Microsoft Xbox 360 Wireless Adapter
Drives:    HDD Total Size: 4460.9GB (7.6% used)
Info:      Processes: 234 Uptime: 7 min Memory: 1741.9/7983.8MB
           Client: Shell (bash) inxi: 2.2.16

```

---

### Post by micha2358 on 2015-07-12
I managed to get the new Catalyst 15.7 work! Now I have version 15.20.1046 installed. But I have still the black screen/cursor only problem. This is mainly with games using the Unity engine.
Last last time those game worked, was the catalyst driver 14.9. But I don't want to use such an old driver. And I don't think it will work with the new kernel in Ubuntu 15.04.

---

### Post by micha2358 on 2015-07-12
Damn, finally I found a script called unity-configurator. 

[http://www.holarse-linuxgaming.de/wiki/universal_unity3d_configurator](http://www.holarse-linuxgaming.de/wiki/universal_unity3d_configurator)

I changed the screen resolutions for the specific games from full screen to windowed and the games work like a charm!

Since the script lists all Unity-based games, I know now which games use the Unity engine. So I figured out, that some Unity games are working in full screen mode and some games don't work (black screen/cursor only).

Why is that? Any idea? Because it's still not satisfying to play the games in window-mode!

---

