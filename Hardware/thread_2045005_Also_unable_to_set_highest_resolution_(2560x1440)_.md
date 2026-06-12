---
title: "Also unable to set highest resolution (2560x1440) on Dell U2711"
date: 2012-08-20
forum: Hardware
---

### Post by graabein on 2012-08-20
I just got my new U2711 monitor on an Intel Sandy Bridge desktop (integrated) card. I'm using the dual link DVI cable but the highest mode I can set from GNOME 3 system settings display is 1680x1050 pixels.

I changed that to the VGA cable and now I have 2048x1152 pixels. Still, it's about 500 pixels short of native resolution and that kind of sucks. 

So I wonder if anyone have any smart suggestions?

---

### Post by graabein on 2012-10-03
Is it allowed to bump threads on this forum? Or is it frowned upon? Should I try swimming on #ubuntu on irc?

---

### Post by lukeiamyourfather on 2012-10-03
The integrated graphics probably don't support that high of resolution. Or if it does support that high of resolution it might only over certain interfaces like DisplayPort.

---

### Post by MarkX on 2012-10-06
I have ALAWAYS had problems with Ubuntu not detecting one of my monitors. You'd think some geek would have fixed this eternal, serious and most basic Linux problem but they are more into their pointless pet projects to make the next release as unfamiliar and unintuitive as possible. I don't think they are actually capable of writing a program where you can manually select a resolution from a menu, that would be too logical...

You have to do a google for "ubuntu 12.04 resolution" and then you'll find piles of drivel about how to "add some mode to you xrandr" and you'll waste an evening typing more drivel into a "console". This will then appear to work (actually mine often doesn't even do that because the amateur who wrote it ***-umed the fix will work for subsequent releases and it doesn't) but when you reboot your puter it'll be back to the wrong *^%^%&& ing resolution again even though you did everything as instructed. 
I just wasted two evenings trying to fix the resoluton and failed. Tempted to get some Macs and leave all the irritating geekery behind...

---

### Post by lukeiamyourfather on 2012-10-09
> **MarkX said:**
> I have ALAWAYS had problems with Ubuntu not detecting one of my monitors. You'd think some geek would have fixed this eternal, serious and most basic Linux problem but they are more into their pointless pet projects to make the next release as unfamiliar and unintuitive as possible. I don't think they are actually capable of writing a program where you can manually select a resolution from a menu, that would be too logical...

You have to do a google for "ubuntu 12.04 resolution" and then you'll find piles of drivel about how to "add some mode to you xrandr" and you'll waste an evening typing more drivel into a "console". This will then appear to work (actually mine often doesn't even do that because the amateur who wrote it ***-umed the fix will work for subsequent releases and it doesn't) but when you reboot your puter it'll be back to the wrong *^%^%&& ing resolution again even though you did everything as instructed. 
I just wasted two evenings trying to fix the resoluton and failed. Tempted to get some Macs and leave all the irritating geekery behind...

This is dependent upon the graphics hardware and graphics drivers. I'm using a Radeon HD 6970 with the proprietary AMD drivers in the Ubuntu repositories. I can use up to six monitors with whatever resolutions I want using the GUI utility that comes with the drivers. Try the proprietary driver for your graphics card if one exists. Or consider getting a different graphics card if no other drivers exist for it.

---

