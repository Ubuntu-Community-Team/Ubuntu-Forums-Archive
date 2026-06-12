---
title: "Lenovo B570"
date: 2011-12-23
forum: Hardware
---

### Post by vasiliymeshko on 2011-12-23
Hello everyone. I'm looking to install Ubuntu 10.04 on a new Lenovo B570 laptop. So far most of the hardware seems to be working fine from the LiveCD (it even pulled the necessary Broadcom wifi driver) with the exception of display. It is stuck at 1024x768 and the desktop effects cannot be enabled.

lspci gives the following output:
```
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
```

and from lshw:

```
*-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:3000(size=64)
```

Anyone with previous experience. Is proper graphics driver even available for 10.04. Basically I'm not even sure if its worth going trough with the install, or just return the laptop and look for something else.

---

### Post by gleg0515 on 2011-12-27
I'm having the exact same problem from the exact same laptop model, a Lenovo B570.  Namely, that is that the screen resolution is stuck at 1024x768, also the touchpad isn't allowing edge scrolling.

 I chose the cheap Lenovo over the cheap Dell because I thought it would have better Linux support.  My specs are the exact same as those given above.

Any help/advice on the matter would be appreciated.  Thanks!

---

### Post by wnelson on 2011-12-27
Get a more current version 11.10 of ubuntu.

---

