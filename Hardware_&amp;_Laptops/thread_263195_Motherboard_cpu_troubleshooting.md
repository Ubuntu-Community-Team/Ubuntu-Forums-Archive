---
title: "Motherboard cpu troubleshooting"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by NoTiG on 2006-09-22
Hey this isnt an ubuntu problem... its just a hardware problem . I have this amd 2200+ in a motherboard... and if i clock the FSB at the rated speed (133) ... it has stability problems and the computer wont boot.. and it says overclock fail. However, i checked the cpu Temperature and its cool at around 28 degrees C . So because the cpu is cool and its failing that test... does that mean its more likely a motherboard problem than CPU ?

---

### Post by futz on 2006-09-23
> **NoTiG said:**
> Hey this isnt an ubuntu problem... its just a hardware problem . I have this amd 2200+ in a motherboard... and if i clock the FSB at the rated speed (133) ... it has stability problems and the computer wont boot.. and it says overclock fail. However, i checked the cpu Temperature and its cool at around 28 degrees C . So because the cpu is cool and its failing that test... does that mean its more likely a motherboard problem than CPU ?
Check your RAM timings and clock speed/multiplier/HT and etc stuff like that. AMD's can overclock RAM without overclocking CPU, so that's a possibility.

Run Memtest for a few complete passes and if you get ANY errors at all, look for the cause. Takes a long time, but then you pretty well KNOW your RAM is good.
 [http://www.memtest.org/](http://www.memtest.org/)
I have a DFI LanParty mainboard, which has settings for absolutely **everything**, as well as MemTest built into the BIOS.

---

