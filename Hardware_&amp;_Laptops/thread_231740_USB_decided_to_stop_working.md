---
title: "USB decided to stop working"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by xerxesv5 on 2006-08-07
Hi all,

Dapper was working fine up until a few days ago. Something weird has happened to USB in general.

Ports dont seem to like any form of mass storage (my iPod worked before, as did my Flash Disk). The 4-port hub wont do anything at all. lsusb just hangs.

This is all I get when plugging my in iPod (onto the board itself):

```
[17180975.036000] usb 5-1: new high speed USB device using ehci_hcd and address 16
```

Here's a sample of the cruft it's been spewing out (dmesg):

```
[17179616.108000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179617.192000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179634.656000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179635.732000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179635.864000] usb 5-4: device descriptor read/all, error -71
[17179635.980000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179638.984000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179642.824000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179642.824000] hub 5-3:1.0: connect-debounce failed, port 3 disabled
[17179644.132000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179644.356000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179644.612000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179644.868000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179645.124000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179645.380000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179645.636000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179645.892000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179646.148000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179646.436000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179646.436000] hub 5-3:1.0: connect-debounce failed, port 4 disabled
[17179646.436000] hub 5-3:1.0: cannot disable port 4 (err = -71)
[17179651.268000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179651.268000] hub 5-3:1.0: connect-debounce failed, port 4 disabled
[17179651.268000] hub 5-3:1.0: cannot disable port 4 (err = -71)
[17179651.324000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179652.396000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179652.548000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179652.804000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179653.060000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179653.412000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179653.412000] hub 5-3:1.0: connect-debounce failed, port 4 disabled
[17179653.416000] hub 5-3:1.0: cannot disable port 4 (err = -71)
[17179661.572000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179661.576000] hub 5-3:1.0: connect-debounce failed, port 1 disabled
[17179661.576000] hub 5-3:1.0: cannot disable port 1 (err = -71)
[17179661.628000] usb 5-4: reset high speed USB device using ehci_hcd and address 4
[17179663.552000] hub 5-3:1.0: hub_port_status failed (err = -71)
[17179663.808000] hub 5-3:1.0: hub_port_status failed (err = -71)

...snip (dozen or so more times)...

[17179667.140000] hub 5-3:1.0: connect-debounce failed, port 1 disabled
[17179667.144000] hub 5-3:1.0: cannot disable port 1 (err = -71)

```

Can't seem to find any solution. Can't think how I could have blown up the hardware - its all working on a different system. I've googled and searched the forum, nothing useful. Any ideas?

Thanks!
- xerxesv5

---

### Post by huygens on 2006-08-14
Hi,

Seems you have a *friend* with the same problem: [http://www.ubuntuforums.org/showthread.php?t=234095](http://www.ubuntuforums.org/showthread.php?t=234095)

Perhaps, you could join the other thread. Or you can continue using yours and maybe answer the same questions I have asked to Mooie.

Huygens

---

