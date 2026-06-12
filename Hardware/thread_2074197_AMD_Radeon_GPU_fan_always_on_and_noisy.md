---
title: "AMD Radeon GPU fan always on and noisy"
date: 2012-10-21
forum: Hardware
---

### Post by circlemaster on 2012-10-21
Hi all.

As the title says I have this problem with my Radeon card here on the stationary computer, I don't have it with my laptop which uses a Mobility Radeon.
I had the problem in 12.04 and was hoping that it would be resolved since I upgraded to 12.10, but it hasn't.

Here's some info on the card:
```
lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]
	Subsystem: XFX Pine Group Inc. Device [1682:2991]
	Kernel driver in use: radeon
```

I've tried this but it gives me permission denied:
```
sudo echo low > /sys/class/drm/card0/device/power_profile
```

---

### Post by Linuxisfast on 2012-10-21
Have you tried using AMD Catalyst drivers?

---

### Post by 2F4U on 2012-10-21
If you are using the open source ATI drivers, this article describes some tweaks that can be used:

[http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/](http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/)

---

### Post by circlemaster on 2012-10-21
> **Linuxisfast said:**
> Have you tried using AMD Catalyst drivers?

I have, but I rather do it the free way.:guitar:

---

### Post by circlemaster on 2012-10-21
> **2F4U said:**
> If you are using the open source ATI drivers, this article describes some tweaks that can be used:

[http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/](http://www.techytalk.info/ubuntu-open-source-ati-radeon-driver-power-usage-tweaks/)

I went with solution #1 and it's less noisy now, still a bit but should I be worried? If it's only the fan then it would mean better cooling right?

Thanks so much for this simple guide.:popcorn:

---

