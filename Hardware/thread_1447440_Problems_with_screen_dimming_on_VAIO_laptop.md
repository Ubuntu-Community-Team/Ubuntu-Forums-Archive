---
title: "Problems with screen dimming on VAIO laptop"
date: 2010-04-05
forum: Hardware
---

### Post by teo_rossi on 2010-04-05
I'm running Lucid fully updated on a VAIO CW2C5E.

When I hit the Fn + F5/F6 to adjust backlight I get the following behavior:
1) The bar is at its maximum (if I increase more it glows). To decrease it completely I have to press the key 37 times, but the backlight only decreases at the 33rd, 35th and 37th hit. The bar reduces alternatively by a small amount and a bigger amount.

2) With the bar at its minimum, I have to hit Fn+F6 52/53 times to reach its maximum, while backlights increases only on the 1st/3rd and 5th hit. The bar increases and then reduces by a small amount with two subsequent hits.

Any ideas on how to solve this?

---

### Post by Greenwidth on 2010-04-05
Might be a screen EDID problem, see:
[http://www.linlap.com/wiki/sony+vaio+cw](http://www.linlap.com/wiki/sony+vaio+cw)

---

### Post by teo_rossi on 2010-04-05
Well I actually have a custom EDID extracted from windows because I needed it for X to work. I also tried the method described in [nvnews forum]("http://ubuntuforums.org/Well%20I%20actually%20have%20a%20custom%20EDID%20extracted%20from%20windows%20because%20I%20needed%20it%20for%20X%20to%20work.%20I%20also%20tried%20the%20method%20described%20in%20nvnews%20forum") and it worked. Anyway some weeks ago I noticed that after an update the backlight OSD came up when I pressed the keys, so I deleted the scripts I created, but left the nvidia_bl module, and I get this behavior.

Is there a configuration file for gnome-power-manager or whatever app controls this settings that I can mess with? It seems the dimming is working but needs to be configured properly.

---

### Post by teo_rossi on 2010-04-07
I noticed that in
```
/sys/class/backlight/nvidia_backlight
```
the file max_brightness reports 127, but the actual brightness values are from 0 to 10.
So the point is that by pressing the key combination the brightness is increased by 5 points, while it should be incresed by 1 point only. How can I fix this?

---

### Post by teo_rossi on 2010-04-07
I've found a decent solution following this post. 
I modified some of the paremeters in nvidia_bl.c source file, so that the brightness values match the ones of gnome-power-manager. Now every time I press the hotkey backlight is changed correcly.
I attach the patch file. Please notice that values could be different with other laptops.

---

### Post by Cuppa-Chino on 2010-04-10
> **teo_rossi said:**
> Well I actually have a custom EDID extracted from windows because I needed it for X to work. I also tried the method described in [nvnews forum]("http://ubuntuforums.org/Well%20I%20actually%20have%20a%20custom%20EDID%20extracted%20from%20windows%20because%20I%20needed%20it%20for%20X%20to%20work.%20I%20also%20tried%20the%20method%20described%20in%20nvnews%20forum") and it worked. Anyway some weeks ago I noticed that after an update the backlight OSD came up when I pressed the keys, so I deleted the scripts I created, but left the nvidia_bl module, and I get this behavior.

Is there a configuration file for gnome-power-manager or whatever app controls this settings that I can mess with? It seems the dimming is working but needs to be configured properly.

how did you extract it and how did you apply it? I have similar problem on a vaio with lucid -- mine runs an ati card but the screen EDID / DDC is a sony botch job

---

### Post by teo_rossi on 2010-04-11
I followed the instructions in [this post]("http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22") to extract the EDID from the Windows 7 partition. They refer to an nvidia card, so I'm not sure they'll help you with your problem. If you have problems with the windows program, you can also try with a software called Phoenix.

---

