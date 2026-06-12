---
title: "Samsung 990 Pro NVMe read/write speed issues"
date: 2024-08-01
forum: Hardware
---

### Post by testuser123452 on 2024-08-01
I have a seeedstudio odyssey blue j4125 v2 - mini pc with frigate NVR installed. Ever since I loaded up this Samsung 990 Pro via the NVMe port as my secondary drive, I have very slow write speeds per frigate logs. For some reason, it takes 1-5 whole seconds to copy over a few megabytes of an MP4, which creates compounded issues when dealing with many cameras. I tried different mounting suggestions with my fstab, such as barrier=0 and async options, but with no luck. The firmware for my NVMe drive is also up to date. 

What sort of troubleshooting could I do to figure out the abysmal r/w speeds for this drive?

---

### Post by currentshaft on 2024-08-01
ext4

---

### Post by testuser123452 on 2024-08-01
This is EXT4

---

