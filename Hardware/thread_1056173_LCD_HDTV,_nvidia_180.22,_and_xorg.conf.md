---
title: "LCD HDTV, nvidia 180.22, and xorg.conf"
date: 2009-01-31
forum: Hardware
---

### Post by malfet1066 on 2009-01-31
Hello,

I've been having trouble getting the nvidia 180.22 drivers to work on my intrepid installation. I have an ASUS P5N7A-VM motherboard with an embedded Nvidia 9300 graphics chip, but I'm fairly certain that the problem is actually my display, which is a Dynex DX-LCD42HD-09 television (which uses a Prima LCD, I'm told).

When I boot up my computer, I get the ubuntu loading screen and then nothing, just black. Keyboard input is getting processed, I just can't see what's happening. Ctrl-Alt-1 takes me to a fully functioning text console. My log file shows that Xorg loaded up just fine.

I suspect that the problem is my LCD's display settings, which I think is not getting detected right by the Nvidia driver when it generates a new xorg.conf file for me.

The Monitor section of xorg.conf is as follows:

```
Section "Monitor"
  Identifier "Monitor0"
  VendorName "Unknown"
  ModelName "Unknown"
  HorizSync 28.0 - 33.0
  VertRefresh 43.0 - 72.0
  Option "DPMS"
EndSection
```

I'm still pretty new to Ubuntu (though troubleshooting this has taught me a lot) so it's very possible that I'm missing something completely, but what I'm reading on the forums seems to indicate that my problem might be in my sync and refresh rates. Is that likely? If so, is there a way I can figure out my displays settings? The manual says nothing and there's no EDID data.

Thanks!
malfet

---

