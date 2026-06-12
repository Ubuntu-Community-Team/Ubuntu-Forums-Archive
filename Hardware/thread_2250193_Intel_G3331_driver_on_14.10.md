---
title: "Intel G33/31 driver on 14.10"
date: 2014-10-27
forum: Hardware
---

### Post by Trucoto on 2014-10-27
Hello, I upgraded from Ubuntu 14.04 and now the video performance is horrible. Just typing this is lagging. My configuration is:

```
$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard [1043:82b0]
	Kernel driver in use: i915

```

I don't seem to have any special driver running, should I? What can I do to restore the old performance?

---

