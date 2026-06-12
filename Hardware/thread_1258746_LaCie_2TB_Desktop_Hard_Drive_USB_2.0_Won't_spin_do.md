---
title: "LaCie 2TB Desktop Hard Drive USB 2.0 Won't spin down"
date: 2009-09-05
forum: Hardware
---

### Post by mande01 on 2009-09-05
Hello,
I have this:
2TB LaCie Desktop Hard Disk USB2 EU 
**Item Number (SKU):** 301405E 
**Serial Number:** 1242807214080FR 

Connected to one of two machines:
IBM thinkpad T30 with FreeNAS
Dell Dimension C521 with ubuntu 9.04

It is basically a 2x SATA to USB controller with 2 x 1TB drives in it.

The drives are Samsung something. On there own I can fully control them.
Once connected through the LaCie box no joy.
I can read and write but its the power management I want.
The things stay spinning the whole time!!! Fan, drives, the little blue light.

I got this off the controller board MS-M E198407 but Google is not providing any luck.

Anyone out there with one of these that have managed to spin them down?
Anyone out there that could help me figure out what to do to get it to spin down?

I have no problem taking it apart again to get chip names and number if needed.
Thanks for reading,
Der

---

### Post by mande01 on 2009-09-06
Ok,
Can anyone here recommend an enclosure that would be good?
There isn't one listed in the hardware compatibility thread.

Thank you,
Der

---

### Post by Whiffle on 2009-09-06
If you can stop it with this:
```

sudo sync
sudo sdparm --flexible --command=sync /dev/yourdrive
sudo sdparm --flexible --command=stop /dev/yourdrive

```

Then this might work:

[http://www.linuxquestions.org/questions/linux-hardware-18/howto-spin-down-external-usbfirewire-hard-drives-on-idle-593192/](http://www.linuxquestions.org/questions/linux-hardware-18/howto-spin-down-external-usbfirewire-hard-drives-on-idle-593192/)

---

