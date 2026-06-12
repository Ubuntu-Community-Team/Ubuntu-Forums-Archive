---
title: "Mobility Radeon 9000 Resume issues, PCMCIA Kernel Freeze"
date: 2011-10-12
forum: Hardware
---

### Post by Mediarocker on 2011-10-12
Hey there guys, I've been tinkering with Ubuntu for a long time now and have just about no idea what to do anymore (I have been trying everything that has been suggested by the community. Maybe I'm not doing something right?). I've been trying to get it to play nice with my Radeon 9000 among as well as my PCMCIA bus.

First the Radeon issue.

The system boots and shuts down normally, I had an issue in 10.04 where I would have to boot into FailsafeX in order to get my graphics to display at all. When I upgraded to 10.10 the issue with boot disappeared, however I have some quirks during resuming after Suspend, Hibernate, and DisplayOff and during screen saver operation (after approximately 5 minutes.)

Whenever the device resumes, It goes through a quick command line and then seizes with a distorted white screen with several black lines across it, this leads me to believe the Radeon card failed to wake up properly and stopped responding to X. It seems the computer resumed normally, however I am not able to see what is going on.

Whenever I close my display and the kernel executes displaypoweroff, it seems to do that properly (because the display actually turns off and the backlight shuts off) however whenever I open the screen it turns on the backlight, but fails to display any image.

During screen saver display it functions normally for a short while, allowing me to return to the desktop normally and resume whatever I was doing, however after about 5 minutes or so, it will hang, and will not respond to any key presses (besides power off) My CPU fans resume normal operation turning on and off as needed despite the hangs.

Now on to another issue. I have a WPC54GS card, it responds as a broadcom device and requires the broadcom device drivers. Despite my best tries, after manually installing the repositories responsible for the broadcom proprietary drivers, it now hangs kernel on boot with the card inserted and instantly in OS upon PCMCIA activation. It seems whenever the card is inserted it now freezes kernel, and I have to hard shut down and start it up again. Whenever it boots it goes through normal boot procedures, powers on the PCMCIA bus and shortly after it hangs. I'm thinking of just getting another card...

I'm new to troubleshooting Linux (especially since I never really had any issues with it previously...) so any help would be greatly appreciated. I do not know where I can find the trouble logs to confirm or deny my suspicions and give you guys more useful information.

Device: Dell Insprion 8200
Proc: Intel Pentium 4M @ 1.8GHz Speedstep Enabled (x86)
Ram: 512MB DDR
Display: Dell Ultrasharp UXGA display @ 1600x1800
Graphics Card: ATi Mobility Radeon 9000 64MB
OS: Ubuntu 10.10 Maverick
Kernel 2.6.35-28-generic
Wireless Card: WPC54GS v12


This is all the information I can pull off the top of my head since I have no networking on my Ubuntu laptop since I'm not where I can hook it up to my router...Hope this helps.

---

### Post by Mediarocker on 2011-10-13
No ideas where to start? Anyone?:confused:

---

### Post by Mediarocker on 2011-10-28
Any ideas guys? I've been trying solutions on other posts, but nothing seems to work.

Any place I can pull a log?

---

