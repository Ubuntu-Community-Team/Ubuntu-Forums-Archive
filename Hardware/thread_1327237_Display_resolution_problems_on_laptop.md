---
title: "Display resolution problems on laptop"
date: 2009-11-15
forum: Hardware
---

### Post by Prima on 2009-11-15
Hey!

I've got a problem with the resolution on my laptop. I'm running with ubuntu 9.04, and a laptop with Intel's own graphic processor "GMA X3100". 

The problems started after yesterday, when i connected and used a projector with the computer for a while. After i disconnected it, and rebooted, the screen display was 4:3, and not 16:10 (it's a 15,4" 16:10 laptop display). 

The only opti[FONT=Verdana][SIZE=1]on i have with 16:10 is 640x400, which anyone knows is far to small :-), otherwise i can only get 4:3 with for example 1280x1024 (highest). 

I'm fairly new to ubuntu, and would like to know if anyone has a solution for me. Probably what i need is to install different drivers or such? 

Cheers / Simon


---


[B][SIZE=2]Solution: 

Edit "/etc/X11/xorg.conf" and remove the line   "[/SIZE][/B][/SIZE][/FONT]**[FONT=Verdana][SIZE=2][COLOR=#000000]Virtual	1152 1632[/COLOR][/SIZE][/FONT]**[FONT=Verdana][SIZE=1]**[SIZE=2]", and the line above and below it. This seems to remove the 4:3 setting that was set when i plugged in the projector.[/SIZE]**
[/SIZE][/FONT]

---

