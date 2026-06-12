---
title: "No sound from Built-in card"
date: 2010-03-27
forum: Hardware
---

### Post by kellanium on 2010-03-27
I'm running the AMD64 bit version of 9.10 on a desktop with an old MSI K8N Neo4 motherboard with an nvidia nforce4 ultra chipset. The sound is not working. Is there a driver for this? i tried downloading the proprietary one ubuntu reccomends but it didn't work, even after reboot.

---

### Post by kellanium on 2010-03-27
if it helps anyone, this is my output for lsmod

```
Module                  Size  Used by
binfmt_misc            10220  1 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
ppdev                   8232  0 
nvidia              10316904  36 
parport_pc             37352  1 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
amd64_edac_mod         26688  0 
k8temp                  5504  0 
edac_core              48876  1 amd64_edac_mod
i2c_nforce2             8168  0 
floppy                 65192  0 
usbhid                 43968  0 
forcedeth              61292  0
```

---

### Post by kellanium on 2010-03-27
Fixed! turned out it was a BIOS issue, not linux at all!

---

