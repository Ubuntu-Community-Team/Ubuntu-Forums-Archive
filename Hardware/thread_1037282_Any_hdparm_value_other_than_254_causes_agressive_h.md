---
title: "Any hdparm value other than 254 causes agressive head parking"
date: 2009-01-11
forum: Hardware
---

### Post by seemanta on 2009-01-11
Hi,

I am in the process of patching my laptop against the Load_Cycle_Count issue. In order to do it, I tried first setting the hdparm to 200 under battery power, manually in a terminal. The idea is that once I find it satisfactory, I shall be making the changes permanent within the designated script folders.

However, I realized that no matter what value of hdparm I choose other than 254, I always get VERY aggressive head parking, almost 2-3 times per minute.

Only when I set it to 254, I get ABSOLUTELY NO head parking and the count stays at the same value for all time. But I do need SOME protection when I am on battery. Surely, having no head parking while on battery is not suggested!


So, it is either no parking or aggressive parking for me. No middle ground, :(.  I was hoping I would use a medium value like 200 with around 15 parkings per hour or so while on battery and a value of 254 while on AC.

Can anyone please confirm if that is also the case with their laptops?

regards,
Seemanta

---

### Post by zbry on 2009-01-27
Yes, I have the same problem and there's one more thing: with no head parking the temperature of my hard drive rises dangerously up to even 58°C while the producer's maximum working temperature is 60°C. Once my drive overheated, so I came back to the original settings, choosing frequent parking over overheating.
My hdd is  WDC WD1600BEVT.

---

