---
title: "SATA link power management UNR 9.04"
date: 2009-06-25
forum: Hardware
---

### Post by Ostien on 2009-06-25
I'm trying to squeeze as much battery life out of my Asus 1000HE.  I have been looking at lesswatts.org for tips and it has mostly worked out.

Although enabling SATA link power management policy via echo min_power > /sys/class/scsi_host/host0/link_power_management_policy does not work as the file does not exist in the first place and I can't seem to even create the file in any case.

Is there something I'm missing?  I'm running Ubuntu Netbook Remix 9.04 kernel 2.6.28-11-generic

I've looked around and seen things about ALPM kernel patches but I want to check here first about what exactly to do as I'm not sure how to apply a kernel patch, and even if thats what I need.

Thanks in advance.

---

