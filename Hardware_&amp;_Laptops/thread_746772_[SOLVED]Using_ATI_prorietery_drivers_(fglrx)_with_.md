---
title: "[SOLVED]Using ATI prorietery drivers (fglrx) with Widescreen resolutions"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by Gordone on 2008-04-05
Hi,
just thought I would share my solution to this problem. 

I have an ATI Radeon 9550, which ran like a bomb with my old 17" CRT, using the ATI restricted drivers (fglrx). however I got a new 19" widescreen LCD recently, and hit a snag with my graphics setup. If I used the restricted driver and tried to set up the widescreen monitor (using System->Administration-> Screens and Graphics) the display crashed and I was forced into low graphics mode. However, if I selected the restricted driver I could use the LCD using regular resolutions (such as 1280x1024). Likewise I could use the widescreen resolutions (such as 1440x900), but I then had to use the Open Source ATI driver (which isn't so great). So my best bet seemed to be a slightly distorted resolution.

I carried on fiddling, and I seemed to find a solution. Using the Screens and Graphics configuration window (System->Administration-> Screens and Graphics) I selected my widescreen LCD monitor, with the resolution and refresh rate I wanted (in my case 1440x900 at 60Hz).

I then used a terminal to run the following command:

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

which configures the system to use the proprietary ATI drivers. I then restarted the X server (Ctrl+Alt+Backspace), and I had widescreen resolutions with fglrx!:)

I'm not sure why this works, although I suspect it is something to do with how the Screens and Graphics Window writes to the /etc/X11/xorg.conf file.

---

