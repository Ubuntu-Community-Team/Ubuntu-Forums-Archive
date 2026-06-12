---
title: "Ubuntu support on Centrino 2 (HP dv7t) platform"
date: 2008-08-05
forum: Hardware
---

### Post by dekang on 2008-08-05
Does anyone known when Ubuntu will add support for the newer Centrino 2 platform?  The following devices don't have driver support in Hardy (8.04.1):

$ lspci | grep Unknown
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0649 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4237
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
06:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

---

### Post by zgornel on 2008-08-05
> **dekang said:**
> Does anyone known when Ubuntu will add support for the newer Centrino 2 platform?  The following devices don't have driver support in Hardy (8.04.1):

$ lspci | grep Unknown
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0649 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4237
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
06:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

Probably never. The devices need to be supported into the kernel so unless you install an alpha intrepid or some other distro with a newer kernel, you have no support ...

---

