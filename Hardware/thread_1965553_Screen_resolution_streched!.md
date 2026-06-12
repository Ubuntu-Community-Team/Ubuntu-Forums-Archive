---
title: "Screen resolution streched!"
date: 2012-04-26
forum: Hardware
---

### Post by Stormlord on 2012-04-26
Hi,

A few days ago when I switched on my laptop, I noticed that its display was streched to a point that a great deal of the displayed data were beyond the physical screen's bottom.  Everything was ok from left to right.  The laptop's internal monitor supports resolutions up to 1440x900.  At that resolution everything was so streched that almost one third of the data were beyond the visible bottom.  All these appear from the moment the laptop is switched on.  Not from the moment Xubuntu's video driver is loaded.

Searching the available resolutions in Video settings, I found out that a new resolution had appeared in the list, 1440x1023.  As I said, the laptop's monitor does not support this resolution normally but I switched to that and everything got squeezed back to normal for the first 900 lines.  The remaining 123 (1023-900) are still below the physical bottom of the monitor.

Can anyone help me about his issue?  Is there a chance the internal monitor is not sending its correct EDID when asked?
I know there's this "CustomEDID" command that can be used in xorg.conf in order to force the use of custom timings.  Can this command help things?

Thank you!

Laptop:  Acer 1804WSMi running Xubuntu 11.10.
Graphics card: ATI Mobility Radeon X600

---

