---
title: "Resolution Problem [1024x768 not working]"
date: 2011-01-17
forum: Hardware
---

### Post by altair4040 on 2011-01-17
**Hi **

[B]
Brief:[/B]
I am new to linux  so pardon me if I seem a little dumb.I am running ubuntu along with Windows 7 operating system (Dual Boot). The problem I'm facing concerns the resolution of my monitor. Ubuntu is running on 800X600 resolution. I would like to change it to 1024x768. Though I'm able to change the resolution using "Monitor Preferences", the result is not exactly the way I want it to be. The resolution ( 1024x768 ) works fine in windows, but doesnt seem to work on Ubuntu (or any ubuntu based distro). So far, I am not able to detect the cause. Any help would be appreciated

**Hardware Info:**
Intel Pentium 4 CPU 3.00Ghz
No Graphic Card
Intel Desktop Board D865GBF
(Integrated graphics.. I guess)
512 MB RAM
Samsung CRT Monitor (Syncmaster 591s) [14" or 15"]
Ubuntu 10.10

**Screenshots**

[These screenshots are from linux mint (an ubuntu based distro). I encounter the same problem in ubuntu.]

_Resolution : 800x600_

[[IMG]http://ompldr.org/tNzB2eA[/IMG]]("http://ompldr.org/vNzB2eA")


_Resolution : 1024x768_

[[IMG]http://ompldr.org/tNzB2eQ[/IMG]]("http://ompldr.org/vNzB2eQ")

---

### Post by BbUiDgZ on 2011-01-17
See if there is any drivers for your onboard graphics
administration > hardware drivers

---

### Post by Xantheil on 2011-02-25
Excuse me for bumping a month old topic. I have the exact problem. It's the first time I believe I've been able to get 1024*768 listed as option (with 10.10). 
Like in the screenshots, the screen isn't focused on the monitor. Also, the pointer's location is shown below it's actual position. I tried to adjust it using my monitor, that didn't help, though. I wasn't able to see the top panel.
Really hoping for some reply. 
Thanks!

---

### Post by gordintoronto on 2011-02-25
If you run Accessories/Terminal and enter the command
lspci
the line which includes "VGA" will identify your graphics adapter.

---

### Post by Xantheil on 2011-02-27
Sorry for late reply. It's Intel 82865G. Pretty old. Well, something should work though, hopefully. I've heard there isn't much support for these petty old stuff. 
*Fingers Crossed*

I mean, c'mon 800*600 is so ugly!

EDIT: I tried changing it to 1024 * 768 through xrandr. It looks the same obviously. However, on running it, I found out it had parameter options like Height, Width. Something like those on the monitor. I thought that might help, but I can't figure out how to enter it without altering the rest. Also I noticed in options for my monitor in Factory display timing it shows 53.5k / 84 800*600. Now, I took a look at the factory timings and I couldn't find any with 1024 *768 on it. There was 720*400 and 640*840. I hope that helps some.

---

