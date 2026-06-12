---
title: "Hardware Acceleration Radeon GPU Problem After Upgrade To 20.04.2 LTS"
date: 2021-02-04
forum: Hardware
---

### Post by javierja on 2021-02-04
I recently upgraded to 20.04.2 

I'm running old hardware
Biostare TA880G HD motherboard

[COLOR=#000000][FONT=Verdana]javier@workstation:~$ inxi -G
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] RS880 [Radeon HD 4250] driver: radeon v: kernel 
           Device-2: Advanced Micro Devices [AMD/ATI] Redwood XT [Radeon HD 5670/5690/5730] driver: radeon v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: radeon resolution: 1440x900~60Hz, 1920x1080~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: AMD RS880 (DRM 2.50.0 / 5.8.0-41-generic LLVM 11.0.0) v: 3.3 Mesa 20.2.6 
javier@workstation:~$ uname -a
Linux workstation 5.8.0-41-generic #46~20.04.1-Ubuntu SMP Mon Jan 18 17:52:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
javier@workstation:~$
[/FONT][/COLOR]
I don't know what is happening but any apps trying to use GPU is completely unusable.
Here is the current list:

Discord
Visual Studio Code (Which i really really need for work)
Chrome (had to disable hardware acceleration)

What can I do to fix this? Should I revert to an older kernel?
If so, how?

---

### Post by javierja on 2021-02-06
Problem was with the bios. of course. hardware.

---

