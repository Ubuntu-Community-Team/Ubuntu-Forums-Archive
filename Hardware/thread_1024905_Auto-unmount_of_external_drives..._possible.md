---
title: "Auto-unmount of external drives... possible?"
date: 2008-12-29
forum: Hardware
---

### Post by xmnemonic on 2008-12-29
I'd like to explore the possibility of developing an auto-unmounter for Ubuntu.  I have some idea of how it *could* work, but don't know enough about linux as to whether it's feasible.  How I think it could work:
[LIST]
[*]Auto-unmounter service or kernel module (not sure which would be appropriate, if either) periodically polls external device for reading/writing status
[*]If device is being written to or read, does nothing
[*]If all reads/writes are complete, unmounts, **but leaves icon on desktop**.  Balloon tip (or something less obtrusive, like a yellow dot appearing on the device icon on the desktop) signifies "[Device Label] safe to remove"
[*]Calls to unmounted device are **caught** as long as device is plugged in.
[*]If device is still plugged in and an application attempts to read or write to it, device is mounted again
[/LIST]
Does anyone knowledgeable about linux handling of external drives know whether this would be possible?  Or is there anything like this already in the works?

---

