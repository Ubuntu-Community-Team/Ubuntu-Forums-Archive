---
title: "Lower fps in GLXgears. Problem with animations in gnome. [ATI 4250]"
date: 2013-04-17
forum: Hardware
---

### Post by DisappearingOak on 2013-04-17
Hi,
I'm having an issue with animations sometimes stuttering in Gnome Shell and also stuttering animations in KDE.
Hardware is AMD Phenom 965BE at stock clock of 3.4ghz 4 cores, 4GB RAM, ATI IGP 4250 (512mb shared) on GA-880GM-d2h. Linux Ubuntu 13.04 beta 2 running Gnome 3.8.
I noticed that a lot of the time, animations like switching windows from the Overview would be smooth. But some of the times, they would stutter a bit when choosing new window, but not all the time.
So I ran glxgears without vertical sync and found that it would run at 1903 fps and lower but would drop down to 120 fps with the gears window maximized. I noticed after maximizing the window, the gears move smooth but after a couple seconds, the gears stutter once. And then smooth as before. I've noticed this when maximizing that it does stutter once. As in stops for a split second and goes on, but it is fast so that it looks like a stutter.
```
glxgearsATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
9519 frames in 5.0 seconds = 1903.720 FPS
9521 frames in 5.0 seconds = 1904.061 FPS
3656 frames in 5.0 seconds = 730.943 FPS
650 frames in 5.0 seconds = 129.774 FPS
648 frames in 5.0 seconds = 129.414 FPS
6733 frames in 5.0 seconds = 1346.474 FPS
4657 frames in 5.0 seconds = 931.127 FPS
648 frames in 5.0 seconds = 129.582 FPS
655 frames in 5.0 seconds = 130.926 FPS
655 frames in 5.0 seconds = 130.751 FPS
657 frames in 5.0 seconds = 131.268 FPS
2036 frames in 5.0 seconds = 407.195 FPS
8530 frames in 5.0 seconds = 1705.916 FPS
9036 frames in 5.0 seconds = 1807.191 FPS
9204 frames in 5.0 seconds = 1840.696 FPS
9082 frames in 5.0 seconds = 1816.361 FPS
9104 frames in 5.0 seconds = 1820.722 FPS
9210 frames in 5.0 seconds = 1841.893 FPS
9233 frames in 5.0 seconds = 1846.515 FPS
9195 frames in 5.0 seconds = 1838.849 FPS



```

Then I switched back to the default vsync. It runs excellent at refresh rate with normal window size. After maximizing, it still runs at the same frame rate.
Then I decided to see what would happen when switching between four windows from the overview. It is smooth. But after some time, I switch to a window, and there's stutter in the animation where the window slides to the front of the desktop. And whenever I notice a stutter in the animation, it also shows up in glxgears as a drop in the fps so it falls down to 50, 51, etc. when there's stutter.

```
glxgearsRunning synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
301 frames in 5.0 seconds = 60.127 FPS
300 frames in 5.0 seconds = 59.940 FPS
300 frames in 5.0 seconds = 59.939 FPS
300 frames in 5.0 seconds = 59.940 FPS
300 frames in 5.0 seconds = 59.939 FPS
300 frames in 5.0 seconds = 59.941 FPS
300 frames in 5.0 seconds = 59.938 FPS
300 frames in 5.0 seconds = 59.941 FPS
300 frames in 5.0 seconds = 59.938 FPS
300 frames in 5.0 seconds = 59.829 FPS
300 frames in 5.0 seconds = 59.939 FPS
300 frames in 5.0 seconds = 59.940 FPS
278 frames in 5.0 seconds = 55.446 FPS
259 frames in 5.0 seconds = 51.765 FPS
261 frames in 5.0 seconds = 52.132 FPS
269 frames in 5.0 seconds = 53.636 FPS
273 frames in 5.0 seconds = 54.491 FPS
295 frames in 5.0 seconds = 58.779 FPS
300 frames in 5.0 seconds = 59.903 FPS
297 frames in 5.0 seconds = 59.345 FPS
287 frames in 5.0 seconds = 57.353 FPS
274 frames in 5.0 seconds = 54.612 FPS
259 frames in 5.0 seconds = 51.640 FPS
259 frames in 5.0 seconds = 51.795 FPS
270 frames in 5.0 seconds = 53.831 FPS
283 frames in 5.0 seconds = 56.542 FPS
269 frames in 5.0 seconds = 53.764 FPS
284 frames in 5.0 seconds = 56.725 FPS
260 frames in 5.0 seconds = 51.818 FPS
264 frames in 5.0 seconds = 52.428 FPS
267 frames in 5.0 seconds = 53.376 FPS
276 frames in 5.0 seconds = 55.154 FPS
265 frames in 5.0 seconds = 52.955 FPS
278 frames in 5.0 seconds = 55.535 FPS
297 frames in 5.0 seconds = 59.345 FPS
295 frames in 5.0 seconds = 58.731 FPS
292 frames in 5.0 seconds = 58.353 FPS
293 frames in 5.0 seconds = 58.541 FPS
293 frames in 5.0 seconds = 58.539 FPS



```

I'm not sure what all this means, if anything. But I want to get the stuttering animation issue resolved, because while I love Gnome Shell, I hate having even a slightly jerky experience. It's very annoying over time. My BIOS is up to date (version FF from Gigabyte). Please help me. What do I need to do? Is this stuttering animation issue a bug in the driver? A bug in gnome-shell? And is there a workaround? Thanks.

---

### Post by Yellow Pasque on 2013-04-18
It could be swapbufferswait parameter. Try using this for /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "SwapbuffersWait" "off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by DisappearingOak on 2013-04-18
> **Temüjin said:**
> It could be swapbufferswait parameter. Try using this for /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "SwapbuffersWait" "off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I tried that xorg.conf that you posted. And I think the stuttering animations is more noticeable than ever. And whenever I switch windows, again the glxgears drop down to 50 51 53 fps while switching and the gnome shell window animations stutter noticeably.

---

