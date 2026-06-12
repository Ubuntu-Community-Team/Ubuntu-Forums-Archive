---
title: "Linux mistakes X1250 for X1200?"
date: 2009-12-05
forum: Hardware
---

### Post by The_Pirate_King on 2009-12-05
I have a working dual boot and Catalyst Control Center in Windows recognizes my graphics card as an ATI Radeon X1250. 
However, linux seems to think it is an X1200. 

```
joe@Harold:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

```

I have tried to install the driver for my graphics card several times and it has screwed up my Xorg server causing me to either have to reinstall or accept the lack of hardware acceleration, which is what I am currently doing.  I suspect this is because linux is not recognizing the chipset properly.  Is there any way to solve this issue?

---

### Post by stark222000 on 2009-12-19
yeah if someone could reply to this that would be awesome. i have a compaq 6515b and ubuntu has told me i have an x1200 but i recently looked at the hp site which says that this computer has an x1250. i have ****** up with this before by installing the wrong driver and when i restart it goes to the text based login and i had to reinstall. is there anyway to get the x1250 and if so will ubuntu actually use it or just think it's the wrong one and go to text login?

---

### Post by The_Pirate_King on 2009-12-21
I had the same problem as you did, it went to a command prompt, I was able to fix it but then I didn't have hardware acceleration. 

The whole reason I thought the driver was the problem was that flash windows were flickering, but apparently that's just a problem with Ubuntu. 

Still, I would like to know why windows says it's X1250 and Ubuntu says it's X1200...

---

### Post by Yellow Pasque on 2009-12-21
It just says "X1200 **Series**", which could include X1250, X1270, etc. IIRC, this is what lspci also listed when I had a 690G/X1250 board. If you're still skeptical, uou could also look in /var/log/Xorg.0.log file. Maybe it will be more specific.

---

### Post by coffeecat on 2009-12-21
Ubuntu (Linux) merely reports what the hardware tells it. It's not a case of Ubuntu having hallucinations. :wink:

Have a look here:

[http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#IGP_.28X12xx.2C_2100.29](http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#IGP_.28X12xx.2C_2100.29)

The X1200 and X1250 have the same graphics core and there are only minor differences in performance.

---

