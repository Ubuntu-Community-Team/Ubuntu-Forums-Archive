---
title: "USB device failure? (lsusb)"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by jjalocha on 2007-09-16
My mother moved to a new apartment, and the Canon i550 printer on her Ubuntu 6.06 box stopped working. Sadly, I don't have physical access to the computer, but I have a working ssh connection.

The printer was set-up with Turboprint and worked always flawlessly. CUPS seems to be working fine, guessing from the web-interface output.

When I ask her to plug/unplug the printer, nothing happens with 'lsusb'. I never get anything detected, wherever (from 4 physical inlets) she plugs the printer:

```

$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

She is absolutely sure that the printer is powered. When I ask her to plug the only other USB device she has (a web cam), it gets detected immediately. 

I tried to find some useful output in 'dmesg', but besides the web-cam, I can't find anything that makes sense to me.

So my questions:
[LIST]
[*]Does 'lsusb' necessarily detect all plugged USB hardware?
[*]Does this not-being-detected mean that there's a printer hardware failure?
[*]If no, how can I test the printer setup?
[/LIST]

---

### Post by geraldm on 2007-09-17
The log shows there are 3 busses for usb detected, and lists one device for each, which is
the root hub.  No plugged in devices are detected.
This can happen when the needed modules did not get loaded. Execute the command
lsmod
and check that the module "uhci_hcd" "ohci_hcd" (if usb-1.1) AND if usb-2.0 "ehci_hcd" are loaded
You said the webcam gets detected, so the above may not apply.

lsusb will detect all working usb devices.  If the device is self-powered and turned off, it 
will not get detected.  Test the printer with a different usb cable if possible, as this
could also be the whole cause of the problem.  Test using a port in which the webcam was
properly detected.

Gerald

---

### Post by jjalocha on 2007-09-17
Thank you very much, Gerald, I will test it as soon as I can get my mother to pick up the phone. :)

---

### Post by jjalocha on 2007-09-18
Problem solved!

What happened finally, was that my mother had her printer NOT properly powered. After turning it on, 'lsusb' immediately recognized the device.

As for the (non-)printing problem, for some reason the printer had disappeared from Turboprint's configuration. After adding it again, everything was flowers and happiness.

---

