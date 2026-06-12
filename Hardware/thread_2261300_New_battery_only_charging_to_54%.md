---
title: "New battery only charging to 54%"
date: 2015-01-17
forum: Hardware
---

### Post by philip10 on 2015-01-17
I know there are a million threads that deal with this but they all seem to be caused by either a bad battery or software limiting the charge. AFAIK my laptop doesn't support limited charging and the battery is brand new.

I have recently purchased a high capacity battery for an HP Compaq c700 and I need to know if I should send it back or not.

The battery will only charge to 54% in ubuntu14.04 and live cd14.04.
Under power statistics the battery shows 99.1% capacity.
The battery will show 100% in windows 7 on a different laptop. (without charging it any more)

The old high capacity battery I was using before only charged to 54% and just recently started charging to 57%. It's capacity is around 84%

How can I determine which part is at fault?

---

### Post by weatherman2 on 2015-01-17
If the old battery also only charged to 54% (or 57%) I'd guess the new one isn't bad just based on the fact that it also shows only 54%.  I'd guess it is not being recognized correctly.

The real question is: how long does it really last?  If it's supposed to be a 4-hour battery and it lasts only just over two hours, maybe it is only charging to 54%.  But if it lasts nearly four hours, the battery is probably fine.

---

### Post by philip10 on 2015-01-17
i have 2x 10400mAh and 1x 4000mAh for testing.
the old high cap battery would estimate around 6 hours moderate use from 57% with lowest brightness and cpu voltage. very breifly checking the low cap battery esimated around 3-4 hours from 100% with unknown brightness and idle usage.

I'm about to do some proper controlled testing with all 3 batteries. Will let you know what I come up with.

---

### Post by Bucky Ball on 2015-01-17
Was the original battery the one that came with the laptop (supplied by HP) and is this one the same (supported by HP) or are they batteries from ebay that say they are suitable for your machine?

---

### Post by philip10 on 2015-01-17
I don't know where my old high cap came from but it was not provided by HP. (57%)

The new one is off an ebay like site and is also not provided by HP. (54%)

the low cap is an official HP battery but belongs to a different laptop. (100%)

---

### Post by Bucky Ball on 2015-01-17
> **philip10 said:**
> I don't know where my old high cap came from but it was not provided by HP. (57%)

The new one is off an ebay like site and is also not provided by HP. (54%)

the low cap is an official HP battery but belongs to a different laptop. (100%)

Perhaps that's telling us something.

---

### Post by tgalati4 on 2015-01-17
You would need to keep track of the full charge voltage (around 12.6 VDC, but it could be different depending on how the cells are arranged).  The battery icon has some detailed statistics for charge and discharge and the summary statistics give an estimate of charge capacity versus design capacity.  Perhaps the new cell requires a higher voltage to charge.  Check your wall adapter and see if its voltage is correct.  A failing wall adapter won't provide high enough voltage (under load) to correctly charge a new battery.

---

### Post by philip10 on 2015-01-18
I have made more of an effort to get the same OS running on both laptops. MiniXP with BattStat is giving me a different reading for each laptop with the same battery (55% vs 100%).
 
It looks like the batttery is just being read incorrectly by my laptop.

I managed to borrow a 3 prong power cord for my brand new charger but that didn't charge it beyond the usual 54%

Will test discharge rate properly tomorrow.

Update: Ok the high cap is lasting significantly more than 2x longer than the low cap. That means the laptop is reporting 54% when the battery is actually 100%. A little dissapointing as I was hoping to get a good 8-12 hours moderate use out of one battery. On the bright side though, I have 2x very usable batteries because the old high cap is much better off than I thought.

---

