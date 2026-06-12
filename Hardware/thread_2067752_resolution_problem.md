---
title: "resolution problem"
date: 2012-10-07
forum: Hardware
---

### Post by ARDV on 2012-10-07
hello
i have nvidia gt 430
i have a problem in resolution

i have just 3 available resolution that are not good at all (i can't seee the top bar for example)
when i try to enter my own resolution in nvidia x server settings it doesn't let me do it (it always back to original)

i have a samsung monitor

help me please, i can't use it like this :(

---

### Post by cwsnyder on 2012-10-07
That usually is caused by your monitor EDID not being read correctly or by your video not being set for resolutions/refresh rates actually supported by your monitor.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) is a good wiki for setting your own resolutions.

In order for more help on actually using xrandr or resolutions which might work, you should list your actual model number of your monitor.

---

### Post by ARDV on 2012-10-07
ok, from settings>display i get 3:
1920*1080 (16:9)
1280*720 (16:9)
720*576 (5:4)

my monitor:
samsung LE26r51b

graphic card: nvidia gt430 (installed the latest driver from their website)

---

### Post by cwsnyder on 2012-10-08
According to the user manual on-line, your maximum resolution is 1360x768, with a refresh rate between 60-75 Hz.  From your listed options, the 1280x720 is the maximum display size usable (720p) with the given driver settings.  You can _try_ setting to 1360x768@60Hz or 1360x768@72Hz, but that may not give you a better display, instead, it may cause similar problems to the ones you are describing.

---

### Post by ARDV on 2012-10-08
> **cwsnyder said:**
> According to the user manual on-line, your maximum resolution is 1360x768, with a refresh rate between 60-75 Hz.  From your listed options, the 1280x720 is the maximum display size usable (720p) with the given driver settings.  You can _try_ setting to 1360x768@60Hz or 1360x768@72Hz, but that may not give you a better display, instead, it may cause similar problems to the ones you are describing.

my best display in win7 is:
1202*670
how can i use it in ubuntu??

and i have in win7 a tool that let me choose the exact resolution by arrows, is there any similar way in ubuntu?

---

### Post by cwsnyder on 2012-10-08
Your nVidia settings tool is probably your best tool to set your resolution.  You should be able to use the 1280x720 resolution suggested by the nVidia tools.

You might also try **arandr** from the Software Center or simply the Display tool in your systems settings.

---

### Post by ARDV on 2012-10-11
> **cwsnyder said:**
> Your nVidia settings tool is probably your best tool to set your resolution.  You should be able to use the 1280x720 resolution suggested by the nVidia tools.

You might also try **arandr** from the Software Center or simply the Display tool in your systems settings.

nothing worked, 
the problem that i can't even see the top bar and almost all the left bar

here is the problem in askubuntu
[http://askubuntu.com/questions/198946/manual-resolution-change](http://askubuntu.com/questions/198946/manual-resolution-change)

---

