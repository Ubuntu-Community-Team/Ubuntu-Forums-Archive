---
title: "External monitor font problem"
date: 2009-01-19
forum: Hardware
---

### Post by casanostra on 2009-01-19
Hi all,

When at work, I connect my HP Compaq nw8240 to a HP L1940 LCD monitor at 1280x1024 through a docking station. When elsewhere, I use the laptop's monitor at 1440x900. I never use extended desktop or any other kind of two-monitor setup.

It basically works fine. The external monitor is correctly identified, resolution is remembered between docks (with a minor glitch, though, since resolution is set to 2560x1024, which I guess would be a extended desktop of two 1280x1024 monitors). 

The problem is that fonts are differently rendered on the two monitors. On the laptop they're very clear and a little "bolder", while on the L1940 they appear "lighter" and a little smudged, and definitely less legible. I have set Subpixel smoothing for both displays, at 108 dpi (which was preselected).

Can anyone give me a hint - how can I tweak the fonts on the external monitor?

---

### Post by blackened on 2009-01-19
Have you tried changing the subpixel order at the bottom of Appearance -> Font Tab -> Details when connected to the external monitor?

---

### Post by mcduck on 2009-01-19
You should use the DPI setting that's actually the same as the display's DPI. It's quite unlikely that both displays, running at different resolutions, would have same DPI.

[DPI calculator]("http://members.ping.de/~sven/dpi.html")

I googled the external monitor, seems to be 19". With that resolution, the DPI would be 86.
The laptop's display is 15,4", and with the resolution you are using DPI for it is 110.

Using the correct DPI setting for your resolution/dispaly size is very important when it comes to text rendering and antialiasing. Lot more important than subpixel order.

---

### Post by casanostra on 2009-01-19
Thanks for your replies.

@blackened: Yes, I did try fiddling with the subpixel order settings, but the differences were so small that I just gave up.

@mcduck: Actually, I had a feeling that DPI would have some kind of influence on font rendering. It's just so extremely complex. I tried with 86 DPI, which just looked weird, and then with 88, which looked better. Actually, it's quite a lot better now at 88 DPI, but it's still not as good as on the laptop. Maybe I'm just using some bad fonts.

---

### Post by casanostra on 2009-01-20
I restarted, and the fonts actually look great now at 88 DPI. Problem solved.

Thanks, you two.

---

