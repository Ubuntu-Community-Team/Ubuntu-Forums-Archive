---
title: "Touchpad not detected on 10.04"
date: 2010-04-29
forum: Hardware
---

### Post by nbulchandani on 2010-04-29
Hello,
Just installed 10.04...and the touchpad is not detected...but the good thing is it detects my keyboard directly unlike as in 9.10..any ideas?
Thanks

---

### Post by anglican on 2010-04-30
> **nbulchandani said:**
> Hello,
Just installed 10.04...and the touchpad is not detected...but the good thing is it detects my keyboard directly unlike as in 9.10..any ideas?
Thanks
You don't say which lap-top you have, which would help. However, it's probably just been toggled off and needs turning back on. Often this is [COLOR=Blue]Fn[/COLOR] F7 or [COLOR=Blue]Fn[/COLOR] F8. There should be an icon on the appropriate function key that looks a bit like a pointing hand in a rectangle, [COLOR=Blue]Fn[/COLOR] [that function key] should turn the touchpad back on.

H

---

### Post by epitaph123 on 2010-04-30
Dual boot Vista SP2 & Ubuntu 10.04

If the touchpad is disabled in Vista, when i reboot into Ubuntu it does not recognize that windows has it disabled. So if i hit Fn+F7 to enable it, it shows disabling touchpad when it is already disabled and hitting Fn+F7 again shows re-enabling it but it still doesn't work until i reboot into vista and enable it there.

So if the touchpad is enabled in Vista and i reboot into Ubuntu the touchpad works fine, i am able to enable/disable perfectly. But if its disabled in Vista then Ubuntu can't enable or disable it at all.

This didn't happen in any other version of Ubuntu, only in 10.04

Does anyone know how to make Ubuntu 10.04 recognize that Vista has the touchpad disabled?

---

### Post by StolenPie on 2010-04-30
I'm having the same problem on my Toshiba NB200, this is a reported bug already
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727)

The bottom line is this handy, albeit temporay solution:

```
sudo modprobe psmouse proto=imps
```

---

