---
title: "Monitor resolution not available?"
date: 2018-03-15
forum: Hardware
---

### Post by asearle on 2018-03-15
Hallo Everyone,

I have an older computer which runs completely fine with a standard (older) 1024x768 monitor.

I then tried to connect a 1360x768 monitor using VGA (unfortunately the monitor only has VGA) and found that the computer recognised that a VGA monitor was connected but would only allow a maximum of 1024x768 resolution. This meant that the picture was "stretched" horizontally.

Instinct tells me that I shouldn't bother investigating too much and should stay with the 1024x768 monitor. But maybe someone out there knows of a trick or an extra piece of software which would allow me to set 1360x768? That would be a great help.

Many thanks,
Alan in Cologne

---

### Post by kerry_s on 2018-03-15
you looked in the display settings?

---

### Post by asearle on 2018-03-15
I checked the display settings in the graphical environment. Normally a whole string of settings appear but in that case there were only a hand full of basic settings with 1024x768 being the maximum. Can I get more information from the command line? Or is that more or less the same?

Ah-ha, I just had a thought: The motherboard is AMD and sometimes the display settings are quirky and you need to install AMDs drivers which are then sometimes not available on newer versions of Linux for older hardware. I'll check that and post feedback.

Yours,
Alan

---

### Post by Autodave on 2018-03-15
Couple possibilities:

1. You video card cannot display anything higher than 1024 x 768.

2. You may have a cheap or defective VGA cable. There is one wire in that cable that reports the monitor's capabilities to the video card. If that wire is broken or missing you will not get the new monitor's size recognized.

Do you know what video card is in the machine? Is it the onboard one or is there a separate one?

---

