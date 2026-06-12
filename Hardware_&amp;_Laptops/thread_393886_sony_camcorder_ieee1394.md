---
title: "sony camcorder ieee1394"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by glederfein on 2007-03-26
Hi all!
I just bought an ieee1394 card and inserted it into the computer. I have a Sony DCR-TRV140E camcorder which I want to capture using Kino, but I can't seem to capture it. According to [linux1394.org]("http://www.linux1394.org/view_device.php?id=810") my camcorder "works great". I keep on getting errors in Kino about raw1394 etc. I tried changing permissions recreating the file but nothing seems to help. I checked out if the card is detected using "lshw" and I get:
```

 *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: a
                bus info: pci@02:0a.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:fea00000-fea007ff ioport:dc00-dc7f irq:169

```. I think that means it's detected.
Can somebody please help me?? :(

---

