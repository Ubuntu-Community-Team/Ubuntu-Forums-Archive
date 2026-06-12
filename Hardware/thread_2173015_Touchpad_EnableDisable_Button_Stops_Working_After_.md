---
title: "Touchpad Enable/Disable Button Stops Working After Suspend"
date: 2013-09-07
forum: Hardware
---

### Post by warnellg on 2013-09-07
I'm running Ubuntu GNOME 13.04 on my Lenovo U410 laptop. This machine has a hardware button that is supposed to enable/disable the touchpad (it shares the F6 key).


When I power on the machine, the button works as expected (i.e., it toggles enabling/disabling the touchpad with each press).


If I then close the lid and open it later (suspend/wake up), the button stops working: pressing it has no effect.


I've verified that I can use ```
modprobe psmouse
``` and ```
modprobe -r psmouse
``` to still enable/disable the touchpad when this happens, but I was hoping someone might know of a way to get the button working again.


If it makes any difference, I also get the following output just after opening the lid, before GNOME takes over (also appears in the output of dmesg):
```
ata2.00: failed to enable AA (error_mask=0x1)
```

Thanks in advance for any suggestions!

---

