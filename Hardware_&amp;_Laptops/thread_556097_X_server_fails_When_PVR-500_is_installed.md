---
title: "X server fails When PVR-500 is installed"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by hungrybastard on 2007-09-20
I have recently installed Edgy 7.04 on an i386 Athlon system. I had been successfully using the nvidia drivers for the Geforce FX5200 video card I am using. Everything was running well up to this point. When I add the haupage pvr-500 and boot, I get an error that the x server failed to start.

The warning and errors from the output file are as follows:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from path
....
(WW) NVIDIA: No matching Device section for instance (BusID PCI:4:0:0) found
(EE) No deviced detected

Fatal server error: no screens found

Is there some kind of conflict between the two devices? I have tried several other PCI slots but with the same result. Also, the Nvidia card uses and AGP slot. Not sure if that makes a difference.

Not sure where to go with this. Any suggestions are appreciated

Edit: When I pull the PVR-500 out, all is well again so it is definitely something w/ the card.

---

### Post by dcstar on 2007-09-21
> **hungrybastard said:**
> I have recently installed Edgy 7.04 on an i386 Athlon system. I had been successfully using the nvidia drivers for the Geforce FX5200 video card I am using. Everything was running well up to this point. When I add the haupage pvr-500 and boot, I get an error that the x server failed to start.

The warning and errors from the output file are as follows:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from path
....
(WW) NVIDIA: No matching Device section for instance (BusID PCI:4:0:0) found
(EE) No deviced detected

Fatal server error: no screens found

Is there some kind of conflict between the two devices? I have tried several other PCI slots but with the same result. Also, the Nvidia card uses and AGP slot. Not sure if that makes a difference.

Not sure where to go with this. Any suggestions are appreciated

Edit: When I pull the PVR-500 out, all is well again so it is definitely something w/ the card.

Put both cards in and - in a terminal - run:

```
sudo dpkg-reconfigure xserver-xorg
```

Chances are the new card is changing the Interrupts so you need to let your system redetect you new config.

You could probably lock the original video care interrupt in your BIOS if you knew exactly what you were doing.

---

