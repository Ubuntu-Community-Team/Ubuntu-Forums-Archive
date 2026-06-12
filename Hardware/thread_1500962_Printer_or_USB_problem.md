---
title: "Printer or USB problem"
date: 2010-06-03
forum: Hardware
---

### Post by lsutiger on 2010-06-03
Recently. when I try to print to my printer, I receive a message that the printer is not connected.

When I remove the usb cable from the computer or printer and plug it back in, dmesg returns the following:
```
[109338.783019] usb 1-2: USB disconnect, address 15
[109365.648024] usb 2-5: new high speed USB device using ehci_hcd and address 4
[109365.800239] usb 2-5: configuration #1 chosen from 1 choice
[109365.812412] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[109366.120279] usblp0: removed
[109367.105058] type=1503 audit(1275600955.936:24): operation="exec" pid=8799 parent=8798 profile="/usr/sbin/cupsd" requested_mask="::x" denied_mask="::x" fsuid=7 ouid=0 name="/usr/NX/bin/nxspool"
[109367.112612] usb 2-5: usbfs: interface 0 claimed by usbfs while 'usb' sets config #1

```

I am not sure of what all that means, but looks like the system is messing with the usb...am i correct?

I get the same error (with different numbers) when I try in different ports.

Thank you in advance.

---

### Post by thodges999 on 2010-06-08
Its not clear if when you plug the usb cable back in does the printer work again?

I came across the [[COLOR="Red"]following[/COLOR]]("https://wiki.ubuntu.com/DebuggingPrintingProblems") which at the end of the page refers to getting an audit message in /var/log/messages (as read by dmesg) as you appear to have and suggests a possible fix.

---

