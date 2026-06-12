---
title: "[SOLVED] firewire harddisk issue"
date: 2008-10-13
forum: Hardware
---

### Post by wessel_k on 2008-10-13
Hi,

I'm wondering if anybody can help me out here.
I've bought a 1TB freecom firewire disk (no USB-connectors present, with a SATA drive). It was MAC HFS+ pre-formatted, but I've reformatted it to NTFS and later to FAT32. But it doesn't want to be mounted on my ubuntu machine. The weird part is that we also have a usb/firewire casing with IDE-connector and that one mounts perfectly fine, even if we switch disks.
The only errors I can find at the moment are listed below:

[  190.919443] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[  190.919452] ieee1394: Node suspended: ID:BUS[0-00:1023]
GUID[0001db8000000264]
[  199.782659] ieee1394: The root node is not cycle master capable;
selecting a new root node and resetting...
[  200.054417] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  207.950743] ieee1394: Node resumed: ID:BUS[0-00:1023]
GUID[0001db8000000264]
[  222.064682] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[  222.064693] ieee1394: Node suspended: ID:BUS[0-00:1023]
GUID[0001db8000000264]
[  473.363111] ieee1394: Current remote IRM is not 1394a-2000 compliant,
resetting...
[  473.634731] ieee1394: Node resumed: ID:BUS[0-00:1023]
GUID[0001db8000000264]
[  473.635060] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

A rescan-scsi-bus.sh doesn't help me out either.

The last thing I can find at the moment is the command gscanbus. This gives me a graphical user interface showing the Freecom disk being 'attached' to the ohci1394 module.

I hope someone can point me into the right direction. I've run out of search options. I'm probably overlooking something.

Kind Regards,

Wessel

---

### Post by wessel_k on 2008-10-14
Isn't there anybody who can help me out here?

Regards,

Wessel

---

### Post by wessel_k on 2008-10-19
Nobody there to point me to the right direction?

---

### Post by wessel_k on 2008-10-27
Still nobody that can give me any idee where to look for the solution or something else?

Regards,

Wessel

---

### Post by wessel_k on 2008-10-31
Bump

---

### Post by wessel_k on 2008-12-15
I also posted the question on LQ.org and I got a reaction there.
Check it out [here]("http://www.linuxquestions.org/questions/linux-hardware-18/freecom-firewire-drive-not-mounted-680307/").

Regards,

Wessel

---

