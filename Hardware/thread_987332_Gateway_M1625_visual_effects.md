---
title: "Gateway M1625 visual effects"
date: 2008-11-19
forum: Hardware
---

### Post by skisky on 2008-11-19
I have a gateway m1625 laptop, and I am having issues with my video driver. Linux says that I am using a proprietary driver, and it seems to be limiting my visual effects. For example; my desktop switching does not resemble a cube...and I cannot hold Ctrl and Alt and flip my  cube to the next desktop.

Any other drivers I can use to enable these effects?

---

### Post by cariboo on 2008-11-19
It would help if you let us know what graphics adapter the computer is using. Could you paste the output of:

```
sudo lshw -C video
```

in your next post. The above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

### Post by skisky on 2008-11-19
Thanks for you quick response!

here is my hardware information

*-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx

---

