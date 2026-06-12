---
title: "Acer Travelmate 3022 WTMi display driver"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by JarkkoN on 2006-10-11
Dear experts, 

regarding my Acer travelmate 3022 WTMi and Kubuntu 6.06, I wonder 
which driver should I use for the integrated graphics adapter with Intel 945 GM Express chip set? I can select 945 graphics adapter and then the driver seems to be i820. However, this selection is not testable and it doesn't allow the 1280x800 resolution of the screen. The automatically detected adapter and driver is "VESA". However, this sets the resolution to 640x480. 

How could I get the external monitor to work together with the laptop screen, simultaneously or by switching? Now the image appears in the external monitor exclusively if the monitor is connected during booting. If there is no external monitor during the boot, the image appears on screen without any possibilities to switch it on an external monitor connected after booting. 

I would appreaciate any help.

---

### Post by encompass on 2006-10-11
Not testable?  try it... that is testing isn't it?
If it doesn't work go back to your old setting.  Backup you xorg.conf file... thats all you need to do.

---

### Post by JarkkoN on 2006-10-12
Thanks for help. For most of the available settings, the System Settings/Display/Hardware menu says that this setting can't be tested safely, When testing it anyway and resetting the X server as requested, Kubuntu freezes. A backup copy of xorg.conf must be restored in a text shell to take it back to life. 

There is one setting for which the test can be applied without resetting the X server, but it "doesn't seem to work" according to the system. For one or two others it seems to work, but the only resolution is very low. There seems to be one setting allowing 1024x796, but none allows the 1280x800 that the screen is capable to do. 

So which settings do you use?

---

### Post by encompass on 2006-10-12
I have a totally different setup.  Twin View nvidea.
I am stumped...
But a search fo the forums... goodness, I say this all day...
[http://ubuntuforums.org/showthread.php?t=274398&highlight=intel+945](http://ubuntuforums.org/showthread.php?t=274398&highlight=intel+945)
Seems to work with him for a little program hack...
Hope it helps.
Please report if it does...

---

### Post by JarkkoN on 2006-10-12
Thanks dude! That looks really to be what I was looking for! I will get that package and try how it works. If it doesn't work for me, I'll get back to this, otherwise consider problem solved. 
... 
apt-cache show 915resolution
...
Description: resolution modify tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

---

