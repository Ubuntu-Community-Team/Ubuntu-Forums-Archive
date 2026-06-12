---
title: "Two cards, latest AMD Catalyst 11.4, problems"
date: 2011-05-11
forum: Hardware
---

### Post by Kollad on 2011-05-11
Hello!

I have laptop HP G62, with two cards: Intel Core i3(later Integrated) and ATI Mobility Radeon HD5470(later Discrete).
Before upgrading to 11.04, i was unable to use Discrete card at all. Installing proprietary driver hangs system on boot, so i had to use open drivers, and sometimes use vgaswitcheroo(to turn off Discrete, because of greatly heating).

Now i upgraded to 11.04, installed AMD Catalyst 11.5 driver, and finally my system is using Discrete card.

After reboot
```
fglrxinfo
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5400 Series 
OpenGL version string: 4.1.10666 Compatibility Profile Context

````glxgears` show nearly 2000 fps, Catalyst Control Center successfully installed, and there are few options like antialiasing etc.

The main problem is that when i try to start any game (probably needed much 3D performance, native linux), my system hangs, and help only Hard Reset. Some games via Wine sometimes didn't start at all, with error, something like "OpenGL problems....", but sometimes it hangs the system like native games (tried Counter-Strike).

Also tried native linux Heroes Of Newerth client, game launches, but screen is full of blinking colors, black areas, artifacts etc. BUT! When i turn off full-screen option, in game options, video becomes normal, despite off slow performance (a little bit better, when i was using open driver in 10.10)

Also i had problem with flash, the same blinking artifacts. The solution was to turn off "Hardware acceleration" in flash player properties

Help me solve this! 

Thanks

---

### Post by TheNerdAL on 2011-05-11
This might help: [http://ubuntuforums.org/showpost.php?p=8972359&postcount=3](http://ubuntuforums.org/showpost.php?p=8972359&postcount=3)

---

### Post by Kollad on 2011-05-12
I tried that about half a year before, no help :( That instructions are for only one video card, and catalyst version 10.1.  But i have HD5470, and intel i3 integrated video in switchable graphics mode (set in BIOS by default, no option to change it), and only latest catalyst 11.4, 11.5 have something to handle switchable graphics. All my attempts before, stuck me in "segmentation error" and black screen on boot. Had to reinstall my system many times, tried all catalyst versions from 10.1 - 11.3, but only 11.4, 11.5 don't hang my system to black screen. I don't know what to do :(

---

