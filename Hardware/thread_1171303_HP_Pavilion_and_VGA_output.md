---
title: "HP Pavilion and VGA output"
date: 2009-05-27
forum: Hardware
---

### Post by ojve on 2009-05-27
Hi!

I'm trying to connect my HP Pavilion dv2000 series laptop with my HP w2207 monitor, using the VGA output via an adapter, with no luck. The monitor doesn't even seem to be detected by the OS.

I also tried installing the gnome-randr-applet, but I don't know how to start it or add it to the gnome panel.

I'm guessing I'll have to add something to xorg.conf, but I have no idea what. Anyway, here's how it looks now:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Any help appreciated!

//T

---

