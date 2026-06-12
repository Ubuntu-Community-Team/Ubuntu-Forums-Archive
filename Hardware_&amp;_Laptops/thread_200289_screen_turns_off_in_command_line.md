---
title: "screen turns off in command line"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by galeta on 2006-06-20
hi,
first of all, i am a newbie. i was a such a long time microsoft user and this linux concept totally strange to me for now. but i love it and i'm trying to get used to it.

here is my problem;

when i hit Ctrl+Alt+F1, F2, F3 .. my screen turns off.  i get back the visual interface when i hit Ctrl+Alt+F7.

when i connect an external monitor to my laptop, the screen turns off again but i get black command line on external monitor.  (only when i hit Ctrl+Alt+F2)

i think my laptop thinks that it has external monitors and tries to open command line on external monitors.

i added this lines to my xorg.cong under devices section;

	Option		"ConnectedMonitor" "DFP"
	Option		"IgnoreDisplayDevices" "CRT, TV"

nothing has changed. when i change "ConnectedMonitor"  "DFP" to "DFP, CRT", my laptop uses only external monitor.

how can i solve this?

thanks for your help,
cem.

---

