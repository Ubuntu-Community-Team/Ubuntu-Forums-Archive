---
title: "make usb 2.0 port behave as 1.1?"
date: 2008-05-08
forum: Hardware
---

### Post by insert_name_here on 2008-05-08
Hey,

Is there some software way by which I could get a USB 2.0 port on my laptop to behave as a USB 1.1 port?  

The issue is that I'm using VMware, emulating windows, and VMware cannot handle USB2.0 data speeds in their virtual USB drivers.  So, my device is hooked up to Ubuntu (the host) and transmitting data at USB2.0 speeds, which confuses VMware, which promptly crashes.  So, I want my device to run at USB1.1 speeds.  Is this possible?

---

### Post by prshah on 2008-05-08
> **insert_name_here said:**
> Hey,

Is there some software way by which I could get a USB 2.0 port on my laptop to behave as a USB 1.1 port?  



You can change the setting in your BIOS; for USB, enable "Legacy" mode, or the settings may be called "1.1".

Alternately  (not sure about this one, that's why it's in alternate), you can ```
sudo modprobe -r ehci_hcd
``` CAVEAT: DONT TRY THIS until someone else can confirm if I'm right or wrong.

---

