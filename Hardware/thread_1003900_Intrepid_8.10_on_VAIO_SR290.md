---
title: "Intrepid 8.10 on VAIO SR290"
date: 2008-12-06
forum: Hardware
---

### Post by WiFi Ed on 2008-12-06
Just a quick post to report the successful installation of Intrepid Ibex x64 on my new Sony VAIO SR290 notebook, dual-booting with Vista Ultimate x64.

VAIO specs:
Intel P8600 Core2Duo
4 GiB 800 MHz ram
ATI Mobility Radeon HD 3470 GPU
Intel WiFi 5100
Bluetooth
Synaptics Touchpad

I re-partioned the HD before starting using Acronis Disk Director 10.0 since Vista doesn't like GParted messing with it. After booting up the LiveCD I could see that most, if not all the hardware was detected and supported so I proceeded with the installation. I set up the root, home and swap partitons in the available open space using GParted and completed the installation.

After re-starting, I setup my WiFi connection without any problems and then installed the ATI restricted driver, all available updates, Conky, AWN, lm-sensors, hddtemp, etc. I'm able to see my CPU and HD temps, but no joy with the ATI GPU temp.

I can adjust/mute sound volume with the Fn keys, but the screen brightness keys don't work. I added the brightness applet to the top panel and it works fine so that's good.

The touchpad works well, with the righthand side scrolling functioning just like in Vista. Sensitivity seems about the same.

I haven't tried the Bluetooth functions yet, but the hardware is detected and seems to be running.

Battery life is shorter in Ibex than in Vista, but overall temperatures are about the same. Battery charging works ok too. When I disconnect the AC power, the display auto-dims, but the panel applet will bring it back up if I want it. The panel auto-dims when I leave the notebook alone for a minute or two.

Suspend-on-lid-closing seems to work pretty good so far.

Here's what it looks like:

---

### Post by bvandev on 2009-01-05
I too successfully installed 8.10 on a Vaio SR290.  

One unresolved problem:
1.  The microphone does not work.  I tried it with Skype and Sound Recorder.  There are a few notes on various forums about a bug in Pulse, which is most likely to blame.  

Any help on getting this working would be appreciated.

Thanks.

---

### Post by iBurger on 2009-03-04
I don't want to hijack your Sony thread, but are you confirming that you have full 3d graphics support on the 3470 ATI ?

---

