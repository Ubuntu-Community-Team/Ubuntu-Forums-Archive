---
title: "insufficient SMART reporting (driver?), ASM1061 Chipset"
date: 2017-12-21
forum: Hardware
---

### Post by madumi on 2017-12-21
I'm new to linux, so bear with me...

I have Ubuntu 16.10 server up and running and use smartctl -a to check SMART status.

My SATA controller has the ASM1061 Chipset and I can see some of the SMART report, but it does not show the extended portions (eg. temperature log & statistics).

If I use the same PCI-E SATA controller card in a windows 10 machine with the same HDD, these portions are available... (In my windows 10 machine, the controller uses the 2006 Microsoft driver, 10.0.16299.98)

I would like to check these extended portions of the SMART report in linux. eg. SMART 187 (Number of Reported Uncorrectable Errors)

What do I need to do to gain access to these portions of the report?

Thanks!

---

### Post by madumi on 2017-12-22
OK, my bad...

smartctl -a only reports the main SMART output
smartctl -x reports the larger report (and includes SMART 187)

---

