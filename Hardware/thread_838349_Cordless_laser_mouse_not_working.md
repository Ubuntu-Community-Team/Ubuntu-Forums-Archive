---
title: "Cordless laser mouse not working"
date: 2008-06-23
forum: Hardware
---

### Post by sandman00 on 2008-06-23
Hi,
I just installed Hardy Heron on my Dell d830 laptop. My Logitech MX600 cordless mouse was *not* connected during the install. Now when I connect my mouse, i.e. insert the usb dongle and press the "connect" button on the mouse, it does not work, after several attempts. Any help will be appreciated.
The dongle is detected by ubuntu, but the mouse does not work. My lsusb output is:

```

Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 005: ID 067b:2506 Prolific Technology, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Also, I had installed ubuntu on my older D630 laptop using the same mouse and it was working fine there. The only difference being the mouse was connected at the time of install.

Thanks.

---

### Post by cubeist on 2008-06-23
> **sandman00 said:**
> Hi,
I just installed Hardy Heron on my Dell d830 laptop. My Logitech MX600 cordless mouse was *not* connected during the install. Now when I connect my mouse, i.e. insert the usb dongle and press the "connect" button on the mouse, it does not work, after several attempts. Any help will be appreciated.
The dongle is detected by ubuntu, but the mouse does not work. My lsusb output is:

```

Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 005: ID 067b:2506 Prolific Technology, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

Also, I had installed ubuntu on my older D630 laptop using the same mouse and it was working fine there. The only difference being the mouse was connected at the time of install.

Thanks.

Can you post the mouse section of your xorg.conf file?  (/etc/X11/xorg.conf)

Also, if you have the time, the tutorial link in my signature will get your mouse going...

---

### Post by sandman00 on 2008-06-23
> **cubeist said:**
> Can you post the mouse section of your xorg.conf file?  (/etc/X11/xorg.conf)

Also, if you have the time, the tutorial link in my signature will get your mouse going...

Here are my InputDevice sections for mouse:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

```

---

