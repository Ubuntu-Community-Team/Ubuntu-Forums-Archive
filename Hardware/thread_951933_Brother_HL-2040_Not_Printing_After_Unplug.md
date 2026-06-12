---
title: "Brother HL-2040 Not Printing After Unplug"
date: 2008-10-18
forum: Hardware
---

### Post by greyblitz on 2008-10-18
Hi All,

I am consistently having problems with my Brother HL-2040 running off Kubuntu 8.04. I'm not sure if Kubuntu has anything to do with it, but I hope that I'm not the only one having this problem. 

The printer is connected via USB. Whenever the power goes out, or when I unplug the computer for a while (say an hour), then plug it back in, the printer turns on even though I haven't turned on the computer. It is as if I had unplugged the printer itself then plugged it back in. After this, I am unable to print anything whether from the desktop computer directly, or another computer via sharing. The job sits there processing indefinitely.

The first time I fixed it by formatting and reinstalling Kubuntu. The second time I replaced cupsd.conf with cupsd.conf.deafault and it worked. Is there some way I can fix this? Or perhaps some setting?

Any help is much appreciated!

Edit: since it is really important to have my printer running I have been trying to fix it as well. This time I replaced the cupsd.conf and it didn't work. I did notice that it doesn't show the printer as being connected to the USB, it shows it under "Other", and lists the URI as: hal:///org/freedesktop/devices/usb_device_* (where * is some long code).

---

