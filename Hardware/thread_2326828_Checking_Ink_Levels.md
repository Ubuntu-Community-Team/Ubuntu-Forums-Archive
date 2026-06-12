---
title: "Checking Ink Levels"
date: 2016-06-05
forum: Hardware
---

### Post by anon_private on 2016-06-05
I have an Epson Stylus SX 100 printer connected to my pc

In tools, I can clean heads, configure, etc, but I cannot check ink levels.

Is there a method of checking the ink levels?

In addition, I know that it Windows the chipped cartridges cannot be refilled, is this true in kubuntu?

Thanks

---

### Post by X-RED_Tech on 2016-06-05
As far as I know the driver for some Epson models has that option. Yours most likely hasn't. we have an old BX300F at the office and it's the same as yours but fortunately the ink levels can be monitored in the printer's settings menu (LCD panel). 
Regarding refilling it depends on the printer's firmware, not driver or OS. I seriously doubt the Linux driver - provided by Epson - would 'unlock' any feature 'locked' in Windows.

---

### Post by anon_private on 2016-07-02
I can check the ink level using a command line line utility (escputil). But I need to locate a path that includes a recognised path from a hard drive folder. The only path I can find is from the CUPS utility that gives usb://EPSON/Stylus%20SX100?serial=KQEZ387420&interface=1. But this is not a proper path from the disk and is not recognised..

Advice please

---

### Post by Linuxisfast on 2016-07-02
Epson L800 comes with Ubuntu drivers and utility to check ink and clean heads.

---

### Post by X-RED_Tech on 2016-07-02
> **anon_private said:**
> Advice please

Already given but ignored: You're wasting your time. It's either on the driver or it isn't.

---

### Post by Linuxisfast on 2016-07-02
> **anon_private said:**
> I can check the ink level using a command line line utility (escputil). But I need to locate a path that includes a recognised path from a hard drive folder. The only path I can find is from the CUPS utility that gives usb://EPSON/Stylus%20SX100?serial=KQEZ387420&interface=1. But this is not a proper path from the disk and is not recognised..

Advice please

Check the path indicated in your driver control panel. Usually its usb.

---

