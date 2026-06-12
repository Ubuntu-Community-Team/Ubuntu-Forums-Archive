---
title: "tv-out problem, nvidia"
date: 2009-06-08
forum: Hardware
---

### Post by tommah04 on 2009-06-08
hey all, just switched from an ATI radeon graphics card because nvidia seems to work better....

I dual-boot ubuntu and vista and with the radeon I was able to choose a "Force TV Detect" option since I have an old tv, I guess the s-video signal doesn't go through all the way or something, but using that option worked fine.

but I can't find an option like that on the Nvidia... but I click the "detect display" button, the tv flickers but then the computer says it was disconnected.... is there a way to force the detection like on the radeon?

cause that'd be awesome

thanks in advance

---

### Post by tommah04 on 2009-06-09
I hate bumping, but................bump

---

### Post by tommah04 on 2009-06-11
one last bump, then I'll take it as a "no"

---

### Post by jocko on 2009-06-11
Try this:
```
gksudo gedit  /etc/X11/xorg.conf
```

Add this to either the "screen" section or the "device" section:
For a display connected to a vga connector + tv out:
```
Option "ConnectedMonitor" "CRT,TV"
```
Or a display connected to a dvi connection + tv out:
```
Option "ConnectedMonitor" "DFP,TV"
```
That will override the monitors that are actually detected and use the specified ones in stead.
You can find more in [nvidias manual]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/appendix-b.html").

---

### Post by tommah04 on 2009-06-11
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-s$
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



thanks for the response, but I'm not really sure where to add it....anywhere, or just at the end of any section?

---

### Post by jocko on 2009-06-12
> **tommah04 said:**
> thanks for the response, but I'm not really sure where to add it....anywhere, or just at the end of any section?

Anywhere within the device section or screen section should work, so try like this:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
[COLOR=Blue]    Option         "ConnectedMonitor" "CRT,TV"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-s$
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by tommah04 on 2009-06-13
that didn't seem to work :-\

quite frustrating, I must say

---

### Post by tommah04 on 2009-06-14
ok, so wierdly enough it just started working.... I don't think I Changed anything since the last time I restarted, but oh well I'm not complaining....

but now I have a new problem.... I have my desktop extended (monitor left, tv right) and everything works fine, I can move between then flawlessly.... but the launch bar that I have at the top doesn't show up.

when I use the compiz cube, it shows up on every other workspace, but when I stop on it, it doesn't show up anymore..... any ideas?

---

### Post by tommah04 on 2009-06-14
nevermind, I restarted again and it worked.... weird
 

thanks all

---

