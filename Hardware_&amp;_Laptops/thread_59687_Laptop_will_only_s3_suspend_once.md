---
title: "Laptop will only s3 suspend once"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by Rob2687 on 2005-08-25
I have a compaq evo n600c and for some reason it will only suspend once. If I put it into suspend a second time it will just hang with the screen off and the power light on forever.

Heres the syslog....
```
localhost gdm[6343] Master suspending...
localhost postfix/master[7669] reload configuration
localhost dhclient Internet Systems Consortium DHCP Client V3.0.1
localhost dhclient Copyright 2004 Internet Systems Consortium.
localhost dhclient All rights reserved.
localhost dhclient For info, please visit http://www.isc.org/products/DHCP
localhost dhclient 
localhost dhclient irda0: unknown hardware address type 783
localhost dhclient sit0: unknown hardware address type 776
localhost dhclient irda0: unknown hardware address type 783
localhost dhclient sit0: unknown hardware address type 776
localhost dhclient Listening on LPF/eth0/00:02:a5:c0:11:21
localhost dhclient Sending on   LPF/eth0/00:02:a5:c0:11:21
localhost dhclient Sending on   Socket/fallback
localhost dhclient DHCPRELEASE on eth0 to 192.168.1.1 port 67
localhost postfix/master[7669] reload configuration
localhost ifplugd.hotplug[9473] Stopping ifplugd for eth0
localhost kernel uhci_hcd 0000:00:1d.0: remove, state 1
localhost kernel usb usb1: USB disconnect, address 1
localhost kernel uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
localhost kernel uhci_hcd 0000:00:1d.1: remove, state 1
localhost kernel usb usb2: USB disconnect, address 1
localhost kernel uhci_hcd 0000:00:1d.1: USB bus 2 deregistered
localhost kernel uhci_hcd 0000:00:1d.2: remove, state 1
localhost kernel usb usb3: USB disconnect, address 1
localhost kernel uhci_hcd 0000:00:1d.2: USB bus 3 deregistered
localhost syslogd 1.4.1#16ubuntu6 restart. 
```

---

