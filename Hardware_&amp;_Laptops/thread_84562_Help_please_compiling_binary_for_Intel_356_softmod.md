---
title: "Help please: compiling binary for Intel 356 softmodem"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by mtron on 2005-10-31
Hi fellow ubuntuers!

i'm currently on holidays at my parents house (with a 56k modem connection, and only a ubuntu install, cd. so i can't download the required build tools to make my module for the 536 EP softmodem.

The card shows up in the ubuntu device manager, but it's not detected by gnomeppp...

running scanmodem, i got:

Providing detail for device at PCI_bus 0000:00:0a.0
Communication controller: Intel Corp. 536EP Data Fax Modem
SubSystem 16be:1040 Creatix Polymedia GmbH V.9X DSP Data Fax
Modem 0000:00:0a.0 0780: 8086:1040
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at e2000000 (32-bit, non-prefetchable) [size=4M]
Capabilities: [e0] Power Management version 2

so, the necessary driver source for my ubuntu standard kernel, version 2.6.12-9-386, would be: 
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng)

Could someone please compile the source (make 536) and upload the binary to rapidshare or send me the binary by mail ?

Many thanks!

mtron

---

