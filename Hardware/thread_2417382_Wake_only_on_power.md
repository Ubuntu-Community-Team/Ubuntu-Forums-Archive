---
title: "Wake only on power"
date: 2019-04-23
forum: Hardware
---

### Post by hoochshepherd2 on 2019-04-23
So my laptop keeps waking in my laptop bag from my usb mouse.  I've been trying to disable wake on anything but power, but failing.

I've seen a waft of threads and no go. Mostly because they are older and using old file structures/locations of things to be changed.

I did have some limited success editing [COLOR=#D4D4D4][FONT=&quot]/sys/bus/usb/devices/1-1/power/wakeup. [/FONT][/COLOR] but that only lasted till I rebooted and all changes were reverted.  And I had issues finding the correct spot to put a script to be executed on boot.

At this point, I'd be ecstatic with boot on wake only!
Any help to this end would earn my undying appreciation... Mainly because I have lid close = power down...

If any of this matters, I'm running mate on the 19.04, and using the 5.0.9 kernel.

---

### Post by hoochshepherd2 on 2019-04-27
So if anyone comes into the same problem I did...  

There are answers all over the internet basically saying:

Open proc/acpi/wakeup
decide what you want to disable.  For me it was XHC. 
Test with echo XHC >/*proc/*acpi/wakeu
If it works, add to etc/rc.local

My problem was that rc.local didn't exist, as apparently that system was abandoned..?

It turns out that while it's not the system used, it still works.

Just create a new one, and treat it as a bash script and make it executable!.

Perfect!

---

