---
title: "Firewire iPod not mounting."
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by imaek on 2005-05-29
I've been trying to go by this tutorial: [http://ubuntuforums.org/showthread.php?t=36632](http://ubuntuforums.org/showthread.php?t=36632)
and it tells me that my iPod will mount on /dev/sdc2 - it doesn't.  I've asked a few people around IRC, and so far I've gotten a few tips:

Do "dmesg | grep 1394" - I get this:
```
ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[fc9ee000-fc9ee7ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00308d0120d2c43e]
ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node removed: ID:BUS[0-01:1023]  GUID[00308d0120d2c43e]
ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[000a2700025751c0]
ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ohci1394: fw-host0: Unexpected PCI resource length of 1000!
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[fc9ee000-fc9ee7ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00308d0120d2c43e]
ieee1394: Node added: ID:BUS[0-01:1023]  GUID[000a2700025751c0]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
``` 
...I don't speak that language.

Try tail -f /var/log/messages and then plug in your iPod - nothing.  I tested a USB device and I got something, but I get absolutely nothing when I try my iPod.


**_ANY**_ HELP would be appreciated as I am very agitated and growing more so by the minute.

Thank you, anybody
- imaek.
P.S. - I'm on IRC now if anybody needs that.

---

### Post by graabein on 2005-08-09
I'm also having problems with iPod/firewire. 

I get a couple ieee1394 errors when I boot the system. The iPod mounts fine when I first plug it in and later remove it. When I try to do it again without rebooting it does not respond.  :? 

Where should I start looking? Is it my firewire PCI-card that lacks a driver or do I have to look at the mounting part with modules and such? 

I am new to this and some pointers would be great.

---

### Post by macabro22 on 2007-12-22
bumP!

2007. I am having a problem mounting ieee1394 external HD as well. 
I get the same error messages.

---

### Post by RaiD_5 on 2007-12-23
Yes, i also have the same problem

---

