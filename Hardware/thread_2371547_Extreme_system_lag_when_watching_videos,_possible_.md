---
title: "Extreme system lag when watching videos, possible graphics driver problem?"
date: 2017-09-15
forum: Hardware
---

### Post by rody4 on 2017-09-15
So, I bought an Acer laptop, got Linux running on it because I hate Windows 10 and it ran horribly laggy on my machine (8gb of ram, 120GB SSD, Intel Pentium quad core n4200 + Integrated Graphics Intel HD 505) and installed all kinds of distros to see which one I like the most. I tried regular Ubuntu, tried Kubuntu, tried Lubuntu, tried Xubuntu, even tried Linux Mint (Cinnamon, then XFCE) however while all the distros ran very smoothly, and I especially loved Kubuntu and am using it right now, it's so incredibly snappy, fast and beautiful, I am at a loss for words, but one issue I've been having that's been persisting for nearly a month now, is ... every time I watch a video on youtube, or I play a game like Stardew Valley, or I use AnyDesk (a screen sharing program), everything smoothly for a few minutes until it just suddenly gets this major spike in cpu usage where 2 of my cores work at 100%, the entire system becomes so laggy, so unstable and so choppy that not only the video/game/whatever I'm doing lags = EVERYTHING else does. When I check 'top' and the system monitor, whatever I'm running on top has the most CPU usage, meaning if I quit chromium or firefox or whatever browser I use (and I've tried all of them, they all reproduce this issue so it's not the browser) the cpu usage will still be high in the program running after it, which may happen to be Xorg, Skype, whatever. Played around with compositor settings, disabled them completely, changed compositing managers, nope - nothing works. Nothing. It just keeps happening even on Lubuntu. Closing the browser doesn't fix the issue, once it starts lagging it keeps lagging, if I'm lucky it'll 'go back to normal' and CPU will go from 80-90-100% to 4-5% as it usually is. If I'm not, only a restart would stop the lagging .. until it lags again. 

I tried installing different kernels. Nope. Upon installing the latest kernel I got an error in Ukuu that I'm missing 3 firmware for my i915 video card (The HD Integrated Graphics 505) and I thought, finally, this must be the issue, so I installed those. Nope. Still the same. I installed the Intel HD Graphics Update Tool for Linux, installed whatever it offered me, NOPE. Still the same issue. 

I am at my wits end. I have no idea what to do. Just to mention, this issue does not exist in Windows 10. In Windows 10, literally every other issue exists other than this one. ****** drivers, slow system, you name it, but videos run smoothly, AnyDesk runs smoothly and games run smoothly. In Linux, everything works fine BUT the issue I described above. I am not going back to Windows 10, my system is also not dual boot. I honestly have no idea what else to do. I tried distro after distro, tried settings, set CPU governor to performance even .. nothing. I can no longer think of anything. So any help would be highly appreciated. 

I am also not an experienced Linux user, just to throw that out there. Merely a beginner learning along the way. Thank you for taking the time to read this!

---

