---
title: "serial ports exist; CUPS can't see them"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by spipe on 2007-04-10
I've just set up a new ubuntu server, one of whose main duties is to drive a printer (actually, a big old card embossing machine) via the serial port.

The serial port is enabled in BIOS and shows up in dmesg and in setserial; and cupsys is installed, with both the port 631 web interface and gnome-cups-manager working.

When I try to add a printer via either interface, no serial ports appear among the connection choices, just the parallel port.

I've searched the cups documentation, which seems not to contain the word 'serial' in it.  Is there a bit of setup I might have missed, or does cups just not support serial printing (anymore)?  In which case, does anyone have any recommendation on what to do?

---

### Post by spipe on 2007-04-11
Ah, okay, got it. In case it helps somebody else:

```
sudo dpkg-reconfigure cupsys
```

... shows that there's serial port support in CUPS, it's just disabled by default.

---

