---
title: "Ubuntu 8.10 / HP 8710w / Sony SDM-S204"
date: 2009-03-13
forum: Hardware
---

### Post by DerMarkus on 2009-03-13
Hi there,
three days ago I installed Ubuntu 8.10 onto my laptop. It is docked in the HP advanced docking station which has a VGA and DVI output. Also I installed the latest nvidia driver (180.29) for the Quadro FX 1600M GPU.
If I connect my LCD monitor with a VGA cabel with the dockingstation the nvidia-settings gui can find the LCD. Everything works fine. But if I connect the LCD through DVI cabel the LCD is not shown. The electrical part ( LCD, cabel, dockingstation, laptop ) is ok because it runs well under XP. My xorg.conf is the default file created by nvidia-xconfig. Hopefully there is someone out there who can help me to setup the DVI port.

---

### Post by DerMarkus on 2009-03-14
Hi there,
I found the problem myself. The Problem was that ubuntu failed to read the edid information with dvi. So the solution is to read the edid data over the VGA connector and add the following lines into xorg.conf:

Option         "ConnectedMonitor" "DFP-1, DFP-0"
Option         "CustomEDID" "DFP-1:/home/user/edid.bin"

---

### Post by arich57 on 2009-03-16
I'm having the exact same problem. Everything worked under 8.04 but I can only get the VGA on 8.10. Can you explain what you did to fix it? I'm never used edid before. Also, where in the xorg file did you add those lines? I'm pretty new to all of this so the more simple, basic instructions you can give, the better for me.

I'm using a 8710w with a dock and trying to do dual monitors- one DVI and one VGA. The boot prompt and OS loading goes to the DVI but once I'm at the login screen, only the VGA and laptop screens can be used. Thanks for the help in advanced.

-Aaron

---

### Post by arich57 on 2009-03-16
so I figured out where to add the lines to the xorg file but now the resolution on the monitor connected over the DVI is only 640x480. How do I get it so it can be the 1600x1200 it should be? thanks.

---

### Post by arich57 on 2009-03-16
I think my problem is the edid file is bad. When I run get-edid I get an error say "Call failed. Your EDID should not be trusted". How can I get a good one? Thanks.

---

### Post by arich57 on 2009-03-16
I got it. I had to use nvidia-settings to grab a good edid file. After, worked great.

---

