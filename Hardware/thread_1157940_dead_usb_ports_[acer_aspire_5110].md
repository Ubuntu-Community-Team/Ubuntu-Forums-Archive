---
title: "dead usb ports [acer aspire 5110]"
date: 2009-05-13
forum: Hardware
---

### Post by poseur on 2009-05-13
Hi,
 
Since a couple of days the usb ports of my laptop seem to have broken. This first happened on windows, and figuring it was probably related to vista, i took a dive and installed ubuntu. 
 
Now first things first: I like the new os. it takes some getting used to but so far so good..
 
Except the usb ports still not work. There is power on the ports, cause i can still power my laptop cooler and the leds on my usb stick start burning as well if i put it in.
No reponse from the hardware though. my usb mouse doesnt work at all, while it works like a charm on a different laptop [with win XP]
 
I get the following dumps from dmesg after i connect a device: 
 
[ 239.769453] ehci_hcd 0000:00:13.2: port 7 reset error -110 
[ 239.769503] hub 1-0:1.0: hub_port_status failed (err = -32) 
[ 239.973430] ehci_hcd 0000:00:13.2: port 7 reset error -110 
[ 239.973471] hub 1-0:1.0: hub_port_status failed (err = -32) 
[ 240.177411] ehci_hcd 0000:00:13.2: port 7 reset error -110 
[ 240.177442] hub 1-0:1.0: hub_port_status failed (err = -32) 
[ 240.381418] ehci_hcd 0000:00:13.2: port 7 reset error -110 
[ 240.381463] hub 1-0:1.0: hub_port_status failed (err = -32) 
[ 240.381474] hub 1-0:1.0: Cannot enable port 7. Maybe the USB cable is bad? 
[ 240.381498] hub 1-0:1.0: unable to enumerate USB device on port 7 
 
 
any thoughts on this?

---

