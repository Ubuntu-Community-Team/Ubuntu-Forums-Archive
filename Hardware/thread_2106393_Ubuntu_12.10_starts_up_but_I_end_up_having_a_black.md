---
title: "Ubuntu 12.10 starts up but I end up having a black screen in my laptop screen"
date: 2013-01-18
forum: Hardware
---

### Post by thiagomei on 2013-01-18
Hi guys, I'm rather new to the Linux world and am experiencing some problems I'd like to seek help with.

So I recently did a fresh install of Ubuntu 12.10 in my Acer Aspire 4736z, which has Intel GMA4500 chipsets.I had to set 'nomodeset' in the installation part to get through the  installation itself, otherwise I would get stuck with a black  screen.

  It ran smoothly, no problems whatsoever after setting that mode.
  And then when I tried to boot ubuntu for the first time, the same  thing happened right after boot. The screen would turn black with no  backlight on whatsoever. But sounds could be heard no problem. 

  Searching on google for solutions, I was unable to fix it.

  However,I tried plugging an external monitor to the laptop, via VGA,  and it worked well. I could, and still can, see the OS running perfectly  through the monitor but not through the laptop screen. Still, even if I  unplug the monitor, the laptop screen will not display Ubuntu.

  I would like to have my laptop screen display the OS and any help is appreciated. Thanks.

---

### Post by Aergan on 2013-01-19
I have seen this happen with HP 6730 which use Intel 945 express family.
For some reason the external port (VGA) is detected as the primary display. The only way I was able to get it to kind of work was to manually configure an xorg.conf file but I was limited to only using standard resolutions and not the native resolution for the panel.

Sorry that's not much to go on or a proper solution.

---

### Post by irv on 2013-01-19
There were some video issues with 12.10 in most of the Alpha/Beta releases but many were resolved in the finial release. This was the first release I couldn't beta test because of the video issues. I did not have this problem with 12.04. If you continue to have problem with 12.10 and seeing it is a new install, I would start out with 12.04 and see how it works for you. It is a good solid release and is supported a full 5 years.

---

