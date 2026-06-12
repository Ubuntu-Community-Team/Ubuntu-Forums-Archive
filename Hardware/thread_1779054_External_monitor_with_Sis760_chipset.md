---
title: "External monitor with Sis760 chipset?"
date: 2011-06-09
forum: Hardware
---

### Post by Mastus on 2011-06-09
Hi,

I have a Acer Aspire 3003wlmi laptop which (unfortunately) has the aforementioned Sis760 chipset with integrated graphics.

When booting up with vga cable connected (to a lcd tv) - desktop and everything is automatically cloned to both displays. 

Problem is that I seem to have hit the known problem with the memory bandwidth - when playing a video, I have green lines flashing in the screen (in both displays). Video plays fine when using only the laptops internal display. 

This link [http://www.winischhofer.net/linuxsispart1.shtml#13]("http://www.winischhofer.net/linuxsispart1.shtml#13") states that the problem could be solved by just using one display.

Just don't know how to disable the laptop display and only output to external monitor. Fn+F5 blackens the laptop display, but when moving mouse or something similar, it starts back again.

Xrandr states that only "default" display is connected, so I cannot force LVDS off methods. 

Oh, and I have 10.04 Ubuntu in use - no xorg.conf (at least yet). Is disabling the internal display even possible via xorg.conf?

Any help would be very much appreciated.

---

