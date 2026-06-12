---
title: "After installed amdgpu-pro, one of my GPUs couldn't be recognized"
date: 2016-11-17
forum: Hardware
---

### Post by welly50704 on 2016-11-17
I have three rx470
After I install amdgpu-pro, only two can be recognized.
But at recovery mode three can be find!

inxi -G
```

welly50704@welly50704-System:~/&#26700;&#38754;$ inxi -G
Graphics:  Card-1: Intel Device 1902
           Card-2: Advanced Micro Devices [AMD/ATI] Device 67df
           Card-3: Advanced Micro Devices [AMD/ATI] Device 67df
           Display Server: X.Org 1.18.4 driver: amdgpu
           Resolution: 1920x1080@60.00hz
           GLX Renderer: AMD Radeon RX 470 Graphics
           GLX Version: 4.5.13453 - CPC 16.40.5

```

lspci | grep VGA
```

welly50704@welly50704-System:~/&#26700;&#38754;$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67df (rev cf)
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67df (rev cf)

```
How can I solve it?
thanks!

---

