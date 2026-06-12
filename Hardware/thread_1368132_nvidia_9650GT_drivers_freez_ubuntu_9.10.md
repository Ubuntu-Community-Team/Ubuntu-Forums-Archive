---
title: "nvidia 9650GT drivers freez ubuntu 9.10"
date: 2009-12-30
forum: Hardware
---

### Post by petex on 2009-12-30
Hi 

after upgarding to ubuntu 9.10 my laprtop (asus n80vn) stated to have problems with GPU (nvidia 9650GT) system shows artifacts resembling  hmm... small sparkles or just noise?? and than using OS for short time and e.g.  lunching browser or other programs systems freezes.

I did purge old drivers resinatlled new hardware drivers both from terminal and than again via hardware drivers, none of this works. I know many people had this problem and it was suppsed to be gone with nvidia 195.x driveres but it did no good for me. I currently run 195.30 but no matter which drivers i use it still happends.

I also abserved that it seams as noise gets worse at lower frequencies / performance levels
Somtimes when system freezes it will lock the GPU so that the computer boot will freeze at checking NVRAM - in such case i have to disconect power and ejct batter to get the laptop working again


**What seams to help is going into nvidia X server  settings >>powermizer and setting prefferd mode to Prefer maximum performance ** << but i have no clue why it helps? is it conetced to problems with power maagment or ACPI - this artifacts kind of look to me like resulting form some physical / frequency problems but this is only my guess as hostly I'm no expert on such things

---

