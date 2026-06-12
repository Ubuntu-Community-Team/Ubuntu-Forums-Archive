---
title: "usb key mounting horror (hotplug related)"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by burlap on 2004-12-21
The problem is: 
I plug my usb key. It gets mounted (/dev/sda1 at /media/sda1). I unmount and unplug it ("eject" does not change anything, so I skip in the description). I plug it again after more than a few seconds (if I plug it at once it works). It is not mounted (/dev/sda1 does not exist) and hal is in uninterruptible sleep. 

I thought it was a bug, so I have found a similar one (#1727) and reopened it (it was closed becuase reporting person did not provide evidence...). 

However - I've installed backported hotplug 0.0.20040329-16ubuntu2-4.10ubp2 (warty-backports) and played with different sripts to discover that if I run ```
sudo /etc/hotplug/usb.rc restart
``` after I unmount the usb key, it gets mounted again (of course I unplug it and plug it back again) without causing any problems to hal. I'm quite happy with it, but of course I'd like to have it working automatically. 

I haven't tried the trick with warty hotplug (why go back if this works?). In fact I didn't even think to check hotplug scripts before. 

Do you think this may be a bug anyway? If so, where? (hotplug? hal? usb-storage? all?)

Is it possible to tweak hotplug scripts to restart usb.agent each time usb key is unmounted (or rather unplugged)?

---

