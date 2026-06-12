---
title: "Brightness Fn keys working only after resume"
date: 2016-08-24
forum: Hardware
---

### Post by sgiacomel on 2016-08-24
Hi,
I have a Dell Latitude E5430 with Ubuntu 16.04
Intel 3rd generation Graphics card


The brightness fn buttons work only after a suspend/resume.

My current kernel boot line:


```
BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=685eae70-4e8a-42f3-b295-9f8ad51dd690 ro quiet splash acpi_backlight=vendor video.use_native_backlight=1 acpi_osi=Linux i915.invert_brightness=-1 vt.handoff=7
```

And for my video card:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	DeviceName:  Onboard IGD
	Subsystem: Dell 3rd Gen Core processor Graphics Controller

```



Thanks

---

