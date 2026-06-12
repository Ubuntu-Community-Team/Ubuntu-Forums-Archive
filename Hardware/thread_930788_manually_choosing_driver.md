---
title: "manually choosing driver"
date: 2008-09-26
forum: Hardware
---

### Post by ibaniski on 2008-09-26
Hey,

I am running an Ubuntu server machine, and just installed the Intel® PRO/1000 PT Quad Port Bypass Server Adapter as an ethernet card. I installed the appropriate driver (e1000e), but the card is not working (not listed in *ifconfig -a*).

It seems the problem is that the OS does not know which driver to use for this particular hardware (when looking at the device using *lshw* it shows as **UNCLAIMED**). However, when I put a different card that uses the same driver, the card is properly identified and working.

So my question is, how does linux/ubuntu map the probed hardware to a driver? Is there a file that I can manually edit? Can this be done via command line instructions? If not, what are my options for specifying what driver should my card use?

Any responses are appreciated.

Thanks,
i.b.

EDIT:

Solved. Had to modify the driver of the device, so that the OS will choose the correct driver.

---

