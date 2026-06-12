---
title: "(Can't) Mount root fs on an external hard-drive connected to PCMCIA USB adapter"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by yyzyyz on 2007-03-06
Hi,

I have an old Dell 8200 notebook which usb 1.0 ports and a crashed hard drive. I have no plans of buying a new hard drive for the time being and want to use this notebook with Ubuntu installed on an external USB hard drive. Normally, this wouldn't be a problem but USB 1.0 ports make it too slow. Therefore, I use a PCMCIA USB2.0/Firewire cardbus adapter to connect my USB hard drive to the notebook.

Now, with Ubuntu installed on the internal drive, this setup worked fine. However, with the internal drive no longer available, I'm not able to boot from the PCMCIA connected USB hard drive. (Please note that I am trying to boot with initrd from CD/Floppy drive and mount the root filesystem from PCMCIA connected USB drive once the kernel is UP). The problem is that the kernel doesn't see the external USB drive at all upon initialization. How can I extend support for the PCMCIA USB adapter to initrd so that the root partition can be mounted off a USB drive connected to PCMCIA USB adapter?

Thanks.

---

