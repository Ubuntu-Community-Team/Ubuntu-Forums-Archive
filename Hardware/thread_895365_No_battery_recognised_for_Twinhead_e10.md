---
title: "No battery recognised for Twinhead e10"
date: 2008-08-20
forum: Hardware
---

### Post by phpmonkey on 2008-08-20
I'm trying to set up a Twinhead e10 lappie with Ubuntu. But no "battery status" icon appears, and if I add "Battery Charge Monitor" to the status bar and then unplug the power, I just get the icon of the end of a power cord. Just like if you add the monitor to a desktop, not a laptop.

This is annoying, but not a show-stopper. But then, 

when I run

```
sudo dpkg-reconfigure xserver-xorg
```

After configuring the keyboard it drops back to the terminal and I get the message

> xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20080820151304
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device 

Thanks in advance! :)

Jenny

---

### Post by phpmonkey on 2010-10-12
Thought I'd mention that this now works fine in Maverick (and I think it was working in Lucid too).

Hooray for Ubuntu! :KS

---

