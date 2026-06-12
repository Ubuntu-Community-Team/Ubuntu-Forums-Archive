---
title: "Warnings observed in Kern log on connecting iPhone"
date: 2012-01-10
forum: Hardware
---

### Post by nitishmd on 2012-01-10
On connecting apple iphone 3gs in Ubuntu 11.10 im getting the following warning infinitely

xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep

Has anyone encountered this?

Found a few links related to the above warning. But im not sure what the error is.

Can anyone route me to the right direction. If its a kernel bug, then I would like to try to fix it, it would be a good way to learn.

Any help on this would be great. Do let me know if any details are required.



Here are the logs while plugging in and unplugging in the device:


[32150.731175] usb 3-2: new high speed USB device number 3 using xhci_hcd
[32150.756644] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32150.757265] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32150.757985] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32150.759228] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32150.761469] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32150.768213] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32151.140905] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32151.142263] ipheth 3-2:4.2: Apple iPhone USB Ethernet device attached
[32151.158058] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32151.160554] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32151.189625] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32151.190928] ADDRCONF(NETDEV_UP): eth1: link is not ready
[32152.490730] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32153.486326] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32154.485795] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32155.485283] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32156.484991] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32157.484428] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32158.484151] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32159.483394] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32160.482714] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32161.482226] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32162.349795] type=1400 audit(1326096816.067:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/run/udev/data/b8:3" pid=11996 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[32162.351682] type=1400 audit(1326096816.067:30): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/run/udev/data/b8:3" pid=11994 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[32162.351998] type=1400 audit(1326096816.067:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/run/udev/data/b8:3" pid=11997 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[32162.352301] type=1400 audit(1326096816.067:32): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/run/udev/data/b8:3" pid=11995 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[32162.481780] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[32454.461304] ipheth: ipheth_rcvbulk_callback: urb status: -71
[32454.461311] xhci_hcd 0000:0b:00.0: WARN: transfer error on endpoint
[32454.462679] usb 3-2: USB disconnect, device number 3
[32454.483482] ipheth 3-2:4.2: Apple iPhone USB Ethernet now disconnected

---

