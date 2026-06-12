---
title: "How To Set an Unsupported Monitor Refresh Rate"
date: 2013-12-17
forum: Hardware
---

### Post by chris1379 on 2013-12-17
I have a Phillips CRT on an Nvidia NVS210 onboard video chip using the 304 driver. My ideal resolution and refresh rate would be 1280x960 (4:3) @ 65Hz. This works in Windows by overiding the EDID. I have tried some xorg.conf changes but I can't seem to get 65Hz at any resolution. It defaults to 60Hz at 1280x960 which results in flicker.

---

### Post by tgalati4 on 2013-12-17
Did you paste the appropriate modeline in your xorg.conf?

[https://help.ubuntu.com/community/NvidiaResolutionXorgConf](https://help.ubuntu.com/community/NvidiaResolutionXorgConf)


tgalati4@tpad-Gloria7 ~ $ gtf 1280 960 65

  # 1280x960 @ 65.00 Hz (GTF) hsync: 64.81 kHz; pclk: 110.95 MHz
  Modeline "1280x960_65.00"  110.95  1280 1360 1496 1712  960 961 964 997  -HSync +Vsync

Your numbers may be different.

Resolution blues?
Modeline in xorg.conf?
Reboot. Be amazed.

---

### Post by chris1379 on 2013-12-18
Yes, I have tried this. It reboots at 1024x768. I can change it to 1280x960 but only at 60Hz. The Xorg.0.log file indicates:

[ 48774.245] (--) NVIDIA(0): Philips PH107E/S/T7 (CRT-0): 350.0 MHz maximum pixel clock
[ 48774.245] (**) NVIDIA(0): Not using HorizSync/VertRefresh ranges from the EDID for
[ 48774.245] (**) NVIDIA(0):     display device Philips PH107E/S/T7 (CRT-0) (Using EDID
[ 48774.245] (**) NVIDIA(0):     frequencies has been disabled on all display devices.)
[ 48774.247] (WW) NVIDIA(0): No valid modes for "1280x960_65+0+0"; removing.
[ 48774.247] (WW) NVIDIA(0): 
[ 48774.247] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[ 48774.247] (WW) NVIDIA(0):     "nvidia-auto-select".

---

### Post by chris1379 on 2013-12-20
OK, I was mistaken. The refresh rate I want is 70Hz. The only refresh rate listed by xrandr for 1280x960 is 60Hz. Do I have to add this to xrandr first? How?

---

### Post by tgalati4 on 2013-12-21
Did you try to add the modeline using 70 Hz?  Since you mentioned *xrandr*, I presume that you are running dual-monitor.  It's possible that you need to change the refresh rate on your laptop so that the video card can choose 70 Hz as a multiple of the 350 MHz video timing clock.  You may not notice the change in refresh on your laptop, but your video card does.

[https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)

---

### Post by chris1379 on 2013-12-21
I tried adding the 1280x960 70Hz modeline in xorg.conf with the same results. I also tried creating a 10-Monitor.conf file per [this site]("http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/") . Is it possible that the Nvidia driver isn't capable of this resolution at anything other than 60Hz? BTW, it's not a laptop and there is only a single VGA output on this Gigabyte GA-M55plus-S3G motherboard. It runs happily at 1152x864@75Hz but that seems like a really odd resolution. I wanted the 1280 width because it is the width of 720p video, my home theater PC (1280x720), and many laptop screens.

---

### Post by Bucky Ball on 2013-12-21
This:

[http://www.gacosta.net/Linux-Apache-MySQL-PHP/making-ubuntunvidia-recognize-your-widescreen-1366x768-resolution.html](http://www.gacosta.net/Linux-Apache-MySQL-PHP/making-ubuntunvidia-recognize-your-widescreen-1366x768-resolution.html)

Go from step two. It will only work if the res you are after is native to the screen (not the nvidia driver as this fix overrides that's capabilities and edid).

You shouldn't need to add modelines. That course of action can lead to serious headaches!

---

