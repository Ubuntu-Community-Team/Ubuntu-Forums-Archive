---
title: "Probably wrong charge battery state"
date: 2013-07-31
forum: Hardware
---

### Post by demontager on 2013-07-31
I got problem with my laptop Asus UX32 VD, I noticed that battery state showing 91% charge rate when Fully Charged and not 100% as expected. BTW on Win7 seems battery state indication works fine and when it charged showing 100%. I have dualboot so checked found this behavior:
Win7  Linux
40%          36%
75%          69%
95%          87%
100%        91%   

 Also I tried another Ubuntu LiveUSB versions, like 12.04, 12.10 and they showing 91% as well.  Further i did re-calibration - charged and discharged battery 2 times - same 91% on Linux.

Laptop is considered new, 4 months old, Battery Care on Win7 reports:
[COLOR=#000000][FONT=Ubuntu Beta]Design capacity: 48wh[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Current capacity: 46wh[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Wear: 7.6 %[/FONT][/COLOR]

---

### Post by zero2xiii on 2013-07-31
> **demontager said:**
> 
Laptop is considered new, 4 months old, Battery Care on Win7 reports:
[COLOR=#000000][FONT=Ubuntu Beta]Design capacity: 48wh[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Current capacity: 46wh[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Wear: 7.6 %[/FONT][/COLOR]

Well, there is your answer. Linux also has a battery state indicator that should give similar output.

it might be a simple issue of linux comparing the "current charge" with the "maximum charge capacity" and thus you get:
100% - 7.6% wear = 92.4%.
A 1.4% error between linux and windows is nothing major. Especially with such a tiny battery (I mean at 50W a 1w difference is 2%!) One might be more accurate (using more decimals) and thus the 1.4% difference.

You can try and alter the battery info inside the linux system files, but this can be dangerous and really difficult to find and resolve.

Maybe someone else might have a better explanation, but I think it might be age, wear and just a small difference in calculation.

Cheers

---

### Post by demontager on 2013-08-01
Thank you for brief explanation, now it more clear to me why Linux showing 92%. Seems it taking wearing factor in account. Yes, it will be nice to tweak Linux files to show correct charge. If someone has experience i will be highly appreciated for this info.

---

### Post by zero2xiii on 2013-08-01
Hay,

Finding the files you need to edit can be tedious since different make's are located in different places, and not all of them even have the ability to edit this. Since the linux kernel does not support editing the firmware of the battery.

However if you really want to go down that rabbit hole, send me a PM and we can arrange to meet in IRC to try and find the needed files and see if we can squeeze it to be like we want it to be.

Cheers

---

### Post by demontager on 2013-10-19
Just want to update: After installing Lubuntu 13.10 today, battery charge now showing correct charge 100% as on Win7. That's much good an convienient now, thanks to developers.


But, i can also see real capacity as follows:
```

$ watch --interval=5 acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 6520 mAh, last full capacity 5955 mAh = 91%
Adapter 0: on-line
Thermal 0: ok, 48.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 108.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 110.0 degrees C
Cooling 0: pkg-temp-0 no state information available
Cooling 1: intel_powerclamp no state information available
Cooling 2: LCD 0 of 100
Cooling 3: LCD 0 of 10



```

---

