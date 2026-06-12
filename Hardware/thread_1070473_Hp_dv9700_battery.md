---
title: "Hp dv9700 battery"
date: 2009-02-15
forum: Hardware
---

### Post by wardy277 on 2009-02-15
Hi, 

I have a HP dv9700 laptop and everything works great!

Although, i was looking into an app called hardinfo. I noticed that it had info on my battery, it says that its state is charged but the capacity is 3456 mAh / 6000 mHa (57.60%). Doe this mean that my battery is stuck at 57%? is there any way to get it back upto 100%?

Chris

(Ubuntu 8.10 x64)

---

### Post by Astinsan on 2009-06-04
I have a dv9700 and I tend to not pay attention to anything reported by the acpi system. They are usually wrong. (it has gotten much better with 9.04) 

That said:
Lithium Ion batteries have a small charge computer built into them that regulates the charges. It keeps track of every discharge (that drops below the safe voltage for li-ion)
, It keeps track of every regular charge (the prefered charge above 30%), It keeps track of temperatures (safe ,unsafe and critical), There are probably more but I can't think of them all. These are used to set a safe level of charge, recharge or disabled (if critical issues came up). 

Lucky these batteries are fairly cheap these days. You can get a new one for under 70$us.

Or you may be lucky and have a recalled battery. I know mine was. (not sure how lucky though :)

---

### Post by wardy277 on 2009-06-04
nice, thanx.

Are you using jaunty then? i tried it on my laptopn but the internet kept dropping out on me, same with my desktop. Have you had this problem? i dont know if there has been a fix yet.

Chris

---

### Post by Astinsan on 2009-06-08
Jaunty is the version I run. The drop-outs are non existant on my system. 

Hp Dv9720 - Athon 64 X2 - nvidia chipset (7150m) 2 gigs of ram.

Intrepid would not even boot on it because of the nvidia chipset. Had to turn off acpi to get it to boot. These issues are not in jaunty.

---

