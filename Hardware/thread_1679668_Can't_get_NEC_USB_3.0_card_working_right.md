---
title: "Can't get NEC USB 3.0 card working right"
date: 2011-02-01
forum: Hardware
---

### Post by Pernig on 2011-02-01
Hi all,

I recently purchased a PCI Express USB 3.0 card to compliment my new USB 3.0 hard drive enclosure. I am having problems getting it to work. Sometimes the card will work but at USB 2.0 speeds, other times it will not work at all.

There is a message that is showing upon booting the system that I think is related. I managed to find it in dmesg:

[   16.046359] xhci_hcd 0000:02:00.0: can't setup
[   16.046405] xhci_hcd 0000:02:00.0: USB bus 3 deregistered

I pulled this from dmesg just now, and on this occasion the ports aren't working. My hard drive is turned on and plugged in, there is a light on the hard drive enclosure to say it is connected, but nothing else.

Hardware wise I am using an Asus M2N SLI Deluxe. The card is plugged into the uppermost PCI Express x1 slot. The card in question is this:

[COLOR="Blue"][NEC chipset 2 port thing]("http://www.scan.co.uk/products/2-port-lycom-ub-108-v2-superspeed-usb30-(nec)-inc-low-profile-pci-e-host-card")[/COLOR].

I'm not sure but I have a feeling my motherboard might not be up to the job. Perhaps it is too old, needs an update, or the 1x slot isn't enough for it?

Thanks in advance for your help.

---

