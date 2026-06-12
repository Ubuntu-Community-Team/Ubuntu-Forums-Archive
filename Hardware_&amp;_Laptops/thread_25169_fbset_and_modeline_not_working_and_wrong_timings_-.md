---
title: "fbset and modeline not working and wrong timings :-/"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by tommie-lie on 2005-04-09
Hi,

Out of the box, Ubuntu uses the VESA driver for X.org, as my graphics card does not have any driver for 2.6 kernels. Now I want to use the available framebuffer driver. So I built a new kernel (based on 2.6.11) with the appropriate framebuffer driver (kyrofb) and framebuffer console support built in.
The framebuffer console works fine at the desired resolution, but when starting X (in xorg.conf, I selected fbdev as driver), there are bright lines on the right and top borders of the monitor. When trying to shift or scale the image via OSD menu, it seems as if the bright lines are like a barrier, the image won't go beyond the line. In fact, the lines becomes brighter, indicating the electron ray not moving at this point and drawing several lines of pixels to one single line, amplifying the intensity.
I assume that this has something to do with wrong timings, so I tried to change them with fbset and xvidtune. fbset did not result in anything, the only settings that showed some change were the resolution settings and the pixel clock, when changing some of the timing values, nothing happened. When trying to change the timings with xvidtune, it tells me that my hardware does not support changing to this mode, whatever value I try.
So I calculated a modeline with [this tool](http://www.dkfz-heidelberg.de/spec/linux/modeline/) (1280x960 at 90Hz) and it suggested ```
# V-freq: 90.00 Hz  // h-freq: 91.33 KHz
Modeline "1280x960" 184.20  1280 1376 1600 2016   960  960  964 1014
``` as modeline. With this in xorg.conf, X used a completely wrong frequency (something above 110kHz for horizontal frequency) and the monitor, of course, displayed some error message. I already tried playing around with the values in the modeline, but all  the timing values seem to do nothing at all, I cannot see any difference between several values.

The problem with the bright borders because of redrawn pixel lines seems to be unknown on the net, I could not find any solution for this.
My monitor is a Medion 1998ob with a maximum pixel frequency of 202MHz and a maximum vertical frequency of 98kHz, my desired video mode is 1280x960 at 90Hz. I use a Hoary beta from about three weeks ago and don't have the bandwith for a dist-upgrade at the moment.

Everything works fine if I use the VESA driver for X and the standard Hoary kernel, but benchmarks showed that the framebuffer access would be up to twice as fast as the VESA driver.

Thanks in advance,
Thomas

---

### Post by soul_rebel on 2005-04-10
Consider this an "UP"
Have you checked /var/log/Xorg.0.log?

---

### Post by tommie-lie on 2005-04-10
[QUOTE=soul_rebel]Have you checked /var/log/Xorg.0.log?[/QUOTE]It doesn't say anything of interest.
X tries to find the correct timings itself, finds something with 108MHz pixelclock and applies the modeline. When trying to change something with xvidtune, nothing is appended to the log.
No error messages, no warnings, no anything ;-)

---

