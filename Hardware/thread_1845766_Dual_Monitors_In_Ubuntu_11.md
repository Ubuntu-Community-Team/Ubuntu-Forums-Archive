---
title: "Dual Monitors In Ubuntu 11"
date: 2011-09-17
forum: Hardware
---

### Post by voodoochild16 on 2011-09-17
I tried searching on the forum and on google. My second monitor is not fullly detected and this is what it shows in the settings. How do I enable it?. And if I could get it enabled, would I be able to drag program windows into it?. I heard somewhere that there is an issue with that. My video card is a ZOTAC NVIDIA GT218-ION. Thanks in advance for any help or suggestions.

---

### Post by howefield on 2011-09-17
Highlight the disabled monitor and click on the Configure button, select Twinview. This should allow you to move application windows from monitor to monitor.

Make sure the orientation of the monitors is correct and press the Apply button.

You might need to save to /ect/X11/xorg.conf to keep the configuration on rebooting.

---

### Post by voodoochild16 on 2011-09-17
> **howefield said:**
> Highlight the disabled monitor and click on the Configure button, select Twinview. This should allow you to move application windows from monitor to monitor.

Make sure the orientation of the monitors is correct and press the Apply button.

You might need to save to /ect/X11/xorg.conf to keep the configuration on rebooting.

I get no picture at all in my second screen.

I tried to edit xorg.conf in etc/X11/ but for an obvious reason that i am unsure about it wont let me edit it, as I have found code on google to paste into it. I was able to edit it before using some command line in Terminal but I dont remember it. Yeah i'm new to all of this...

So as you can see the second monitor in the image is labeled: CRT-1 with a resolution of 1024x768 and my second monitor is another dell 17" but a different model. When I try to apply the changes I get this error:

Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1280x1024 +0+0, CRT-1: nvidia-auto-select @1024x768 +1280+0' (Mode 2304x1024, id: 50) on X screen 0.

images is attatched of error thingy.

---

### Post by voodoochild16 on 2011-09-17
Any ideas?

---

### Post by Dy1anW on 2011-10-08
I had exactly the same problem as you, and after numerous attempts to get it working I eventually gave up. Twinview usually resulted in my main screen being blank, and my second screen being active; mouse clicks on my main screen would have results in the second. A bit strange, I know. Having separate X sessions wasn't of much consolation either, as on the second screen, windows would be missing decorations (close/minimise/maximise) and I couldn't type anything either.

I saw your post and thought I'd give it another shot; surprisingly it actually worked this time (w00t!).

It seems nvidia-settings misses out a couple important bits of info, so when you "save to configuration file", take a look at the changes first and add/modify these two lines as necessary (in the first "Screen" section):

```
Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-1"
Option "TwinViewOrientation" "DFP-0 LeftOf CRT-1"
```Hopefully that should work. I'm not entirely sure why that last line should even be necessary since the second monitor's position was already described in the metamodes :confused:.

---

