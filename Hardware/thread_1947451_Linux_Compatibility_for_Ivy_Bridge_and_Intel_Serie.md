---
title: "Linux Compatibility for Ivy Bridge and Intel Series 7 Motherboards?"
date: 2012-03-26
forum: Hardware
---

### Post by SemiExpert on 2012-03-26
Now that the i5-3570K and i7-3770K CPUs and several Z77 motherboards have been benchmarked, how much do we know about the Linux Compatibility of Ivy Bridge CPUs and the associated Intel Series 7 Motherboards?  I'm interested in an overclockable desktop that relies solely on Intel HD 4000 graphics.

---

### Post by oldfred on 2012-03-26
The only thing I have seen is this:

[http://www.phoronix.com/scan.php?page=article&item=intel_los_lunas2&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_los_lunas2&num=1)

Which sounds better than most very new hardware not working for 6 months or more.

---

### Post by Mark Phelps on 2012-03-27
> **SemiExpert said:**
> ... I'm interested in an overclockable desktop that relies solely on Intel HD 4000 graphics.

When I was overclocking my Gigabye mobo, I was doing it in Windows and it came with monitoring apps furnished by Gigabyte through which I could monitor core temps.  Also, Catalyst Control Center (also in Windows) provided me a way to monitor the GPU temp as well.

The main concern I would have is with monitoring the temps -- which will increase due to the overclocking.  Newer chipsets require newer sensor modules, and lm-sensors is not always able to keep up.

While it's unlikely you will do any actual damage (especially if you've done overclocking before), without monitoring temps, if you started getting seizing or crashing, you wouldn't know if overheating was the culprit.

---

### Post by SemiExpert on 2012-04-03
The new Intel H77 and Z77 motherboard have been unveiled:  [http://www.techpowerup.com/163336/Intel-Unveils-New-Z77-Motherboards.html](http://www.techpowerup.com/163336/Intel-Unveils-New-Z77-Motherboards.html)  [http://www.techpowerup.com/163509/More-Intel-Desktop-Board-Media-Series-Motherboards-Pictured.html](http://www.techpowerup.com/163509/More-Intel-Desktop-Board-Media-Series-Motherboards-Pictured.html)  I'm wondering if there's any news about Linux support for these motherboards?

---

### Post by SemiExpert on 2012-04-18
Phoronix: [http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1)

---

### Post by MonkeyPaw on 2012-04-19
I'm sure you'll have SOME success, but I generally wouldn't have high-hopes for bleeding edge hardware on Linux, or any other OS for that matter. After all, Intel semi-botched the 60-series release with the SATA corruption issue. The 70-series chipset brings USB3 onboard, so I'm sure other changes are in the mix. As always, buying the newest stuff makes you a beta tester sometimes. I say give it a few months and let the dust settle on any potential issues that would get fixed through driver improvements and BIOS updates.

As for monitoring temps, I'm sure the BIOS has an option to send an alert at a certain temperature, and I think they either auto-throttle or shut down if you start hitting dangerous temps. The main thing to watch for, IMO, is board temperatures. Pulling lots of Watts can really heat up the power delivery components. Obviously, good cooling is important.

---

### Post by SemiExpert on 2012-04-23
[http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1)

---

