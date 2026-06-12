---
title: "&quot;HDMI not connected&quot; after monitor re-start"
date: 2019-04-06
forum: Hardware
---

### Post by dkolars on 2019-04-06
Just had monitor problems...  vertical line on left side of ASUS 27" monitor...  unplugged cable from video card, error message did NOT show vertical line.  Hence, bad card, right?    Had Nvidia card, replaced with AMD...  hey, vertical line still there.  Installed new Dell 27" monitor... Line GONE... bad monitor, contrary to the test results.

BUT, now, when I turn off the monitor, and later turn it back on, I get the "No HDMI signal found" error, and end up rebooting to have monitor working again.

Searched the interwebs for hours, no luck...  Here's what I have for card:

> lspci -k | grep -EA2 'VGA|3D'
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Radeon RX 460/560D / Pro 450/455/460/555/560] (rev cf)
	Subsystem: XFX Pine Group Inc. Polaris 21 XL [Radeon RX 560D]
	Kernel driver in use: amdgpu


Any ideas as to what is causing this problem?  I will not live with it...  I have not yet tried re-installing the  GeForce card that was in there... that will be my next step.

---

