---
title: "from 20.10 to 21.04 dual screen not working anymore"
date: 2021-05-06
forum: Hardware
---

### Post by magowiz82 on 2021-05-06
Hi,
Since upgrade to hirsute (21.04) from groovy (20.10) my hdmi port on my graphic card stopped to work correctly and started to display static effect on second monitor.
Here it is mine videocards:
```
$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
```

I was able to test it with 3 different kernels :
```

5.12.1-051201-generic   # last mainline kernel
5.11.0-16-generic  # last official kernel from hirsute
5.8.0-50-generic  # probably a old kernel still there from groovy

```

Only the older one, 5.8.0-50-generic was working correctly with dual monitor with no issues.
What I want to ask is : which is your advice ? Keeping an old kernel, even if it works, doesn't seem to me a great idea, is there anything I should try to solve or at least to understand what's happening with current kernel ? Is it advisable to report this problem as a bug?

Kind regards

---

