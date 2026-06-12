---
title: "video driver for riva TNT"
date: 2009-04-05
forum: Hardware
---

### Post by amp_man on 2009-04-05
I'm installing xubuntu 8.10 on a friend's fairly old system, and trying to get video working properly. I'm not looking to run compiz or anything like that, just get flash video (e.g. youtube) working properly. I've tried to use the nvidia driver, but I get this message at boot time:

```
nvidia (71.86.04): Installing module.
............(bad exit status: 10)
  Build failed.  Installation skipped.
```

The line from lspci:

[code]01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
	Subsystem: VISIONTEK Device 0002
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at fa000000 (32-bit, prefetchable) [size=32M]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, rivafb
[/quote]

I've also tried the nv driver, but output is choppy and the video size does funky things, it switches between normal size and half size every second or so. Is there any way to get this working? Thanks.

---

### Post by 67GTA on 2009-04-05
The legacy drivers are not compatible with the xorg version in 8.10. They work with 8.04 and earlier. Nvidia decided to stop updating the older drivers. Look for **"**nVidia legacy video support" on the release notes page
**[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)**

---

### Post by amp_man on 2009-04-06
Ah, well that sucks. I think I've got the nv driver working now though, youtube seems to be working.

---

