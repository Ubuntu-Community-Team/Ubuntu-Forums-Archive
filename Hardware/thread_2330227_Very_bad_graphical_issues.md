---
title: "Very bad graphical issues"
date: 2016-07-09
forum: Hardware
---

### Post by leozinho29_eu on 2016-07-09
Hello

I am having graphical issues with many softwares when using Lubuntu 16.04 on my notebook. 

Initially, I tried to find a solution using the Steam forum ( [http://steamcommunity.com/app/221410/discussions/2/358415738201963149](http://steamcommunity.com/app/221410/discussions/2/358415738201963149) ), but looks like it will not be answered. When I did that post, I was not aware that the problematic softwares I cited on the Steam post all function when using Windows XP, so clearly the issue is with Linux, most likely Mesa.

Using some of my Steam post to describe the situation:

Steam: Nearly every button, image or text appears as white, gray or black blocks.
Stellarium: 0.11.6 functional, anything above shows a white screen
XMind: refuses to open
Firefox: gray block in address bar (solved changing gfx.xrender.enabled to false or using a specific theme)
Google Earth: a dark sphere (Earth) appears and I can see only the borders.

Some images showing Steam in Lubuntu and Windows XP:

[http://i.imgur.com/InzQaEh.png](http://i.imgur.com/InzQaEh.png)
[http://i.imgur.com/BXkLA8P.png](http://i.imgur.com/BXkLA8P.png)

The notebook is a Asus M2400N, a 2003 notebook. It has 1248 MB RAM, an Mobile Intel® 855GM Chipset, an Intel® Pentium® M Processor 735 (Warning: pae forced!). The 855GM supports up to OpenGL 1.3.

One thing I remember from my searches about Stellarium is that one post told that Mesa developers had abandoned the 8xx Chipsets (found it: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1286516/comments/4](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1286516/comments/4) ).

If this happened with Ubuntu only, I would perfectly understand: it is made to modern computers, so it is no sense to support 2003 machines. But the very existence of Lubuntu is to give a new life to old computers.

At every Lubuntu boot, some error messages appear. How I am using Windows XP now, I can't copy them. I will edit the post to add them when I reboot the computer. If I am not wrong, they have something to do with graphics.

Edit: the boot is configured "quiet forcepae" and the error messages are:

```
[    2.655990] [drm:intel_set_cpu_fifo_underrun_reporting [i915]] *ERROR* pipe A underrun
[    2.667746] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[   12.802324] asus_laptop: Error calling CWAP(1)
```

---

### Post by mörgæs on 2016-07-09
Hi, you have old Intel graphics which sometimes needs special care. 

I suggest that you click the link in my signature, then 1) run ```
sudo apt-get install xserver-xorg-video-intel
``` and 2) do the changes required for UXA.

---

### Post by leozinho29_eu on 2016-07-09
About xserver-xorg-video-intel, it is already installed. I formatted it 3 times and only in the fourth attempt I noticed this package was lacking. Without it the notebook was non-functional. It is updated too. I hope they add this package in the Lubuntu ISO.

About the guide and uxa change, I noticed no difference. I tried in the config file to choose uxa, sna, off and none (the last 2 should deactivate acceleration). I tried to add a xorg.conf at /etc/X11/ and tried to add a 20-intel.conf at /usr/share/X11/xorg.conf.d/, these options made no visible difference, nor in performance nor in error messages at boot. I am unsure if they worked. All the programs that had errors showed the same errors.

Looks like there is some configuration above the xorg.conf, because creating it made nothing.

---

### Post by leozinho29_eu on 2016-07-11
After searching, I have found a workaround ( [http://askubuntu.com/questions/170668/intel-do-flush-locked-failed-input-output-error](http://askubuntu.com/questions/170668/intel-do-flush-locked-failed-input-output-error) ) that makes most software that was not working to work (looks like XMind issues are a bit bigger), but with much worse performance.

To do this, I have to open terminal, write LIBGL_ALWAYS_SOFTWARE=1 before the name of the program I want to open. Example:

```
LIBGL_ALWAYS_SOFTWARE=1 steam
```

That command opens Steam without graphical errors. I can chat with my friends and I can even open games, as Starbound or Kerbal Space Program, just to see how much seconds it needs to pass one single frame. Ignoring that the frame rate of 0,16 fps, the CPU temperature of 104°C and the fan at full speed, the games are playable (keyboard and mouse are responsive considering the performance) and without graphical glitches.

I have found a workaround, but the performance reached is really problematic. Is there a way to solve the issues and make the hardware acceleration work, relying on the much slower software acceleration is not a good alternative at this case, sadly. The performance hit is really significant.

I still believe the UXA solution will work, however some configuration file is above the xorg.conf, making its creation or edition irrelevant. If I was able to find that particular file I could make hardware acceleration work well. If Windows XP can make the software work, Lubuntu 16.04 can do it too.

---

