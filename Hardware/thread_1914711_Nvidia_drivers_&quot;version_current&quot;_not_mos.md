---
title: "Nvidia drivers: &quot;version current&quot; not most recent"
date: 2012-01-24
forum: Hardware
---

### Post by The Linux Cynic on 2012-01-24
I'm using Ubuntu 10.04 LTS.

I had a problem with webgl in Firefox so I wanted to update my nvidia drivers. The ones I had available through the proprietary driver tool were "NVIDIA accelerated graphics driver (version 173)" and "NVIDIA accelerated graphics driver (version current) [Recommended]". Naturally, I had the recommended version activated, but I found out it wasn't actually the current one.

I did a little more digging and found that there were more recent versions of the driver not being detected. I had to go through the package manager to upgrade the related packages. According to the Nvidia X Server Settings tool (nvidia-settings), I'm now using version 290.10 (the one I installed).

Why arent the most recent drivers recommended or available through the "Hardware Drivers" tool?

I'm using a laptop with GeForce 8400M GS.

---

### Post by The Linux Cynic on 2012-01-26
No one else has this problem?

When I tested other laptops with Nvidia cards, I found the same thing to be true. Why arent the most recent drivers the "current" ones?

---

