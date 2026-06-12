---
title: "PS/2 Mouse don't work"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by paladinhugo on 2005-04-29
Hello!

I've installed Ubuntu Linux 5.04 in an old computer. I have a PS/2 mouse but it seems not to be working. I've tried to use a USB mouse and it did work.
Do I need to install any driver for the PS/2 Mouse to work? Can you help me in what I must do?

Thanks in advance.

---

### Post by heimo on 2005-04-29
Could you open /etc/X11/xorg.conf and find "InputDevice" sections and post here? There should probably be atleast one for your keyboard and one for your mouse,  but if there are even more, post them all.

It's something like this:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
EndSection
``` 

For Device one value couls be /dev/psaux to force PS2. (I can't verify this at the moment.)


Cheers!

---

### Post by GordonInc on 2005-06-20
I have an USB mouse, but using it on PS/2 port because baterries are loaded only on that port (when power is down).
My mouse didn't work after installation of Ubuntu, but there was a surprise when I connect it to USB port! It's working on it. But surprise was greater when I reconnect it on 'power on' to PS/2 port <- it's still working!
After reboot it's still working!  :razz:

---

