---
title: "AMD Radeon drivers and tearing?"
date: 2016-05-18
forum: Hardware
---

### Post by Omegaham on 2016-05-18
I have a Radeon R9 390 graphics card that is currently running what I believe to be the open-source Radeon drivers on Ubuntu 16.04. I have a dual-monitor setup of two HP monitors - one connected to HDMI, one connected to DVI-D. Whenever I open the Dash command or start playing a game on Steam, there is an enormous amount of tearing - horizontal lines that flicker back and forth across the screen. It also tears badly when Ubuntu starts going to sleep after a period of inactivity. Videos on VLC and Youtube do not trigger this tearing.

One suggestion that someone had was to change the DRI from 2 to 3. Looking at ```
man radeon
```, there are a couple of other options that seem reasonable. One of them is "Option Tear-Free," which looks like a really good idea.

Now - how do I actually set these options? In long-past versions of Ubuntu, there was a /etc/X11/xorg.conf file that had all of this. However, current versions of Ubuntu don't seem to have one of those at all. I tried generating one with [this link]("http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file"), and I completely borked the hell out of my installation and had to reinstall (not a big deal, but still irritating). In the past, you would use the proprietary AMD drivers to generate said xorg.conf for you, but again, those proprietary drivers are gone.

Any help would be greatly appreciated and very helpful, as there is literally zero documentation on this for Ubuntu 16.04. Thanks in advance!

Also, doing  ```
lspci -nn | grep VGA
```

resulted in the following message, which is *close* but not quite; I run a 390, not a 290.

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii PRO [Radeon R9 290] [1002:67b1] (rev 80)
```

---

