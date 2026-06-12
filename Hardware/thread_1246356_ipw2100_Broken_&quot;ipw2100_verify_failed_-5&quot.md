---
title: "ipw2100 Broken: &quot;ipw2100_verify failed: -5&quot;"
date: 2009-08-21
forum: Hardware
---

### Post by vagary on 2009-08-21
Hi, I've filed this as a [bug against linux-firmware]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/408631"), but it's not getting any attention, so I thought I'd also pose it as a question:

After I install jaunty on my IBM/Lenovo X31, my wireless network adapter will work for a few hours each boot for the first few weeks. After a few hours it fails with:

$ dmesg | grep 2100
[   13.327281] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   13.327286] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   13.433625] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.434454] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[ 13.434479] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3.fw
[ 8306.362158] ipw2100: IRQ INTA == 0xFFFFFFFF
... (48 lines of this)
[ 8307.162589] ipw2100: IRQ INTA == 0xFFFFFFFF
[ 8307.176398] ipw2100: eth1: ipw2100_verify failed: -5
[ 8307.176463] ipw2100: eth1: Failed to power on the adapter.
[ 8307.176470] ipw2100: eth1: Failed to start the firmware.

But then after a week or two the "ipw2100_verify failed: -5" happens on boot. If I try to reload the module it fails with "Device not found via register read."

I'm starting to think this is bad hardware - how can I diagnose that?

Thank you.

---

