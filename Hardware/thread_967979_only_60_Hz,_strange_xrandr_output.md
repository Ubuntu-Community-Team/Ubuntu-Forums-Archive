---
title: "only 60 Hz, strange xrandr output"
date: 2008-11-02
forum: Hardware
---

### Post by spacy on 2008-11-02
Hi there!

Yesterday I installed Ubuntu 8.10 x86_64 on my machine, finally replacing Windoze Vista.


I have a SAMSUNG SyncMaster 940MW TFT screen connected with DVI to my MSI GeForce 8800 GT. I used the restricted drivers manager and installed the proprietary 177.80 driver with it. The screen resolution was set to 1440x900 by default, which is correct, but only to a refresh rate of 60 Hz, even though my screen can do 75 Hz without problems (tested on Windoze).

Here's the problem:
"System->Settings->Screen resolution" shows 50 Hz and 51 Hz for the 1440x900 resolution.

Now here's what's funny:
Look at the output of xrandr: [http://vba-m.pastebin.com/f10f84dae](http://vba-m.pastebin.com/f10f84dae)
(I tried added some custom resolutions and can#t remove them anymore, so don't worry about these at the bottom).
As you can see, the refresh rates for every mode start with 50 Hz and the values are counting up for every mode. That looks definitely wrong.
How can I add a 75 Hz mode and use it?

Even with "NVIDIA X Server Settings", I only get 60 Hz, even when I select 75 Hz.

---

### Post by spacy on 2008-11-02
OK, after reading "/usr/share/doc/nvidia-glx-177/README.txt.gz" I added
> 	Option	"DynamicTwinView"	"False"
[QUOTE][/QUOTE] to the "Device" section in the xorg.conf file and this solved the wrong refresh rate listing by XrandR and in the gnome display resolution settings. Now I get listed 60 Hz and 75 Hz as it should be, and Compiz Fusion does NO fall back to 50 fps but rather 60 fps (way smoother)

HOWEVER, even if I select 75 Hz now and click on apply, I still end up with 60 Hz. Why?

---

