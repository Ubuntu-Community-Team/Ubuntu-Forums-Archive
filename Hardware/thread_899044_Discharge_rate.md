---
title: "Discharge rate"
date: 2008-08-23
forum: Hardware
---

### Post by goeagles520 on 2008-08-23
Hello,

Is there anyway I can get info about the battery discharge rate? I searched around and cant seem to find a command or widget or something...

Thanks,
GoEagles

---

### Post by Sam Lars on 2008-08-24
What do you mean by the "rate?"
If the power manager icon is in the system tray, you can right click and look at Power History, which has all kinds of good info.
You can install and run (with sudo) powertop, which will show you the wattage and what's waking up the processor.
You can run
```
acpi -b
```
to get info on your battery.
There's also a gnome-panel applet to monitor battery usage.

---

### Post by goeagles520 on 2008-08-25
Thanks sam. I found that powertop gave me the info I needed.:)

---

