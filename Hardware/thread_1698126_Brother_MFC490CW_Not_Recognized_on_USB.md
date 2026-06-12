---
title: "Brother MFC490CW Not Recognized on USB"
date: 2011-03-01
forum: Hardware
---

### Post by MiniVanMan on 2011-03-01
I'm beyond frustrated.  I just loaded Ubuntu 10.04 32 bit onto a new system and can't get the Brother MFC490CW printer to work.  I updated the motherboard and processor in the machine from an old Celeron D to an AMD64 Phenom x2. 

Everything worked just fine on the old system.

Here's my lsusb output.

Bus 002 Device 002: ID 045e:071d Microsoft Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

No printer found obviously.

I get a "MFC490CW printer may not be connected" error when trying to print a test page.  

I'm fairly convinced it's a USB problem.  I've tried swapping USB ports, to include using the one the keyboard and mouse were connected into.

For some reason the computer will not recognize a USB connected printer.  

Any help would be greatly appreciated.

---

### Post by MiniVanMan on 2011-04-05
This is embarrassing, but a pretty good "gotcha".  

What this problem turned out to be was the printer was placed on a pull out shelf and for anybody that has this printer will know is that the USB port is somewhat hidden.  It's also RIGHT NEXT to the ethernet port.  A USB plug fits nicely into an ethernet port.

So, it was actually a matter of it being plugged into the wrong port due to a lack of being able to see back there.  

Why it was unplugged in the first place I don't know.  

Anyway, plug it in to the correct port and everything worked perfectly.

---

