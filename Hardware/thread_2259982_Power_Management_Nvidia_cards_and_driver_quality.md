---
title: "Power Management Nvidia cards and driver quality"
date: 2015-01-08
forum: Hardware
---

### Post by mladen.adamovic@gmail.com on 2015-01-08
Hi guys,

I currently use Radeon R9 280X and when using standard drivers fans are too noisy and when using fglrx it is sometimes buggy.

Questions:
1) Is in general everything OK with Nvidia 7xx and 9xx series? 
2) is power management for those cards as good as in Windows?

Thanks

---

### Post by efflandt on 2015-01-08
I cannot comment on noise level 970/980 other than that many of them do not run the fans at all unless temperature rises above a certain point under load.

I recently installed an MSI TwinFrozr Gaming GTX 750 Ti OC and its fans do not seem to make any noticeable noise at default 32% or when doing benchmarks and it barely bumps to around 34%. It is so efficient that it might not get up to 50 C or just into the low 50's overclocked with barely a few % increase fan speed. And it only uses 60 watts, so my whole PC uses a little over 150 watts max (AC input on Kill A Watt meter) vs. a little over 200 watts with 116 watt GTX 550 Ti. And it idles at about 50 watts vs. 75.

The only momentary snag is that the old nvidia-current (304) driver (and possibly nouveau) in 14.04 does not support Maxwell chips. So nothing installs automatically for these cards, I had to boot into text mode to install drivers. The nvidia-331 works (in 12.04 as well), but to allow overclocking I installed nvidia-346 (currently 346.22) using xorg-edgers ppa. The same likely goes for GTX 9xx series which use the Maxwell chip. [http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item)

Some of these new cards require UEFI, but my MSI has a switch in case its default UEFI/BIOS hyprid mode is not compatible with a BIOS system and the other switch position is Legacy BIOS mode. I have not tried the hybrid mode to see if that works, I simply switched it to Legacy BIOS mode because the newest BIOS for my PC from 2010 does not have UEFI. I have heard of issues for other brands of these new cards on computers without UEFI.

---

