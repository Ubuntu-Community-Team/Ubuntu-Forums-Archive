---
title: "lacie firewire 250gb"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by Anguilla on 2005-05-06
hello everyone!
I have a strange problem till yesterday night my external drive was working perfectly an automounted by gnome!
now I don't know why doesn't work no more!!! and on a win system is immediatly recornized and usable!!!
I tryed to see if was a problem of mounting but by digiting "fdisk -l" I saw thant is not more registred under "sda", so I tried to digit "dmesg" and this is the answer:

ieee1394: Initialized config rom entry `ip1394'
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460300f4b7bd]
ieee1394: Node added: ID:BUS[0-01:1023]  GUID[00d04b511b095b29]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00d04b511b095b29]
ieee1394: Error parsing configrom for node 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Error parsing configrom for node 0-00:1023
ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00d04b511b095b29]

that means nothing for me... some help???
it's strange that from one day to another stops to work...

---

### Post by Anguilla on 2005-05-07
Please someone can help me?? I have a lot of things inside of the disk!

I tried to see in var/log/messages and a I get this: (5 of may is the last day in which the disk was work and 6 the first of not working...)

May  5 15:58:34 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
May  5 15:58:35 localhost ieee1394.agent[7774]:      sbp2: already loaded
May  5 16:04:36 localhost kernel: scsi1 : SCSI emulation for IEEE-1394 SBP-2 Devices
May  5 16:04:37 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
May  6 12:26:26 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
May  6 12:26:26 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]
May  6 21:07:37 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
May  6 21:07:37 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]
May  6 21:22:46 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
May  6 21:22:46 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]
May  7 13:29:26 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
May  7 13:29:26 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]

I searched in google but without a solution...

---

### Post by Anguilla on 2005-05-07
now booting one time with the recover kernel I found another time the disk!!
also with the normal kernel... and so problem solved, but very strange...

---

