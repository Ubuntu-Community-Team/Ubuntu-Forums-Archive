---
title: "Nvidia GTX 580 issue in Ubuntu 11.04"
date: 2011-05-07
forum: Hardware
---

### Post by DIFTOW on 2011-05-07
Nvidia GPU issue - OpenGL working in some applications, and not so good in others.

I have installed the driver over 5 times. Each time, removing it completely and rebooting before running a clean install.

I've used jockey, packet manager, and the .run file from Nvidia's website in terminal.

All 3 delivered unsatisfactory results. While I can run Unity... Anything with 3D graphics (apps requiring hardware acceleration).. render terrible. Constant freezing.

The "additional drivers" window displays the driver as "activated" but then states that it is currently "not in use". How can something be activated but not in use?!

I ended up ending this with a 2nd reinstall of the manual (.run) option.

Some programs like "Amensia: The Dark Descent" run perfect on highest settings and 1920x1080... Some games have a few stutters like "Alien Arena"...

But other applications have bigger issues, or are just completely unplayable.
The worst so far.. is EDuke32. A port of Duke Nukem 3D, that allows it to run natively on Linux. Running Vanilla Duke in OpenGL mode isn't just low FPS, but freezing. Odd freezing because, if i open the dev console.. it instantly unfreezes.

Running EDuke32, with polymer enabled (the updated graphics engine).. seems to reduce the lag almost completely. It is very odd.

Other games, the lag happens on GUIs.. not even the in-game. OpenRA's initial setup menu, lags so bad.. when i move the mouse, its movement is like 3 fps.

Another game with a weird GUI lag.. is "0 AD". The main menu when the game starts, also experiences a low frame rate, indicated by laggy mouse/cursor movement.

If I had to guess.. I would say majority of the lag has to do something with 2D graphics, or legacy support (Older openGL)

After messing with my drivers 5 different ways, I don't think its the drivers. I am running a 64 bit Linux system, so this could be the issue, but if that is the case, I know easy fixes are possible because I've done one for ZSnes way back.

If anyone has any ideas on what the cause could be, or would like to help me.. please don't hesitate. I wasted about 11 hours today on this D:

---

### Post by dtmonterrey on 2011-06-01
Hi

I don't think it has to do with the 64bit thing, I have the same issue on EDuke32 on a 32bit machine with proprietary NVIDIA GeForce 8800 GTS on Natty with Unity

---

