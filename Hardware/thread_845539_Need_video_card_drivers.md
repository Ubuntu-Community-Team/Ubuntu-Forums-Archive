---
title: "Need video card drivers"
date: 2008-06-30
forum: Hardware
---

### Post by strbarrytree on 2008-06-30
Hi i have a acer aspire 5610 laptop, i have ubuntu v 7.04. Im not quite sure what video card i have. Any help on where to get or how to install a video card driver would be nice. thank you

---

### Post by phidia on 2008-06-30
Open a terminal and copy & paste this:
> lspci -v you can look thru that for your video card or paste the output here.

---

### Post by strbarrytree on 2008-06-30
i found this

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

---

### Post by phidia on 2008-06-30
Take a look at the guide [here]("https://help.ubuntu.com/community/Video") and for the specific changes and ways that hardy differs from that [here]("https://help.ubuntu.com/community/XORGHardy").

---

### Post by strbarrytree on 2008-06-30
ok thank you

---

