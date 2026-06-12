---
title: "Input not supported with maximum resolution (Acer H233H)"
date: 2009-03-11
forum: Hardware
---

### Post by ikus060 on 2009-03-11
Hi,

When I set the resolution of my screen to 1920 x 1080, My monitor display 'Input not supported' message. My monitor is a Acer H233H 23" with Maximum resolution of 1920 x 1080 @ 60Hz.

I'm running the latest version of Ubuntu 9.04 Alpha 5.

How to reproduce :
1. Open a user session
2. Go in System -> Preferences - > display
3. Change resolution to 1920 x 1080
4. Click 'Apply' button
5. Monitor show 'Input not supported'

It's make me belive that Hsync or Vsync are not define properly by the monitor of by X.

My monitor specs :

hsync 54.2kHz - 83.8kHz
vsync 49-75Hz

pixel rate 134.6Mhz

I have some problem to read the log, so here it is. (The file was to big so I pull it on a server)
[https://www.entreprisesmd.homeip.net/share/Xorg.txt](https://www.entreprisesmd.homeip.net/share/Xorg.txt)


Thanks to help me solve this problem.

---

