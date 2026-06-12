---
title: "How to run laptop on AC without (dis-)charging the battery"
date: 2017-09-06
forum: Hardware
---

### Post by Blauer Kuckuck on 2017-09-06
Hi everyone,

is it possible to somehow run a laptop on AC power and - without physically removing the batteries - redirect the AC power to the power supply so that the battery is not involved in any charging and discharging cycles?

I have a Lenovo ThinkPad T450s, which is greatly supported by Ubuntu package tlp, which allows for example to set custom charging thresholds. However, I have not yet found a way to completely avoid battery usage when the laptop is plugged in.

Thank you so much for any hint!

---

### Post by Autodave on 2017-09-06
If it is plugged in and fully charged, the battery really isn't doing a thing then : it is neither charging (because it is already charged) nor discharging (because it is running on AC power).

---

### Post by Blauer Kuckuck on 2017-09-06
Thank you! Can I somehow set the point at which the battery stops being charged to a lower point like 80%?

---

### Post by Autodave on 2017-09-06
Not that I know of.  Besides, why would you want to do that? That would only serve to shorten the battery's life. The worst thing you can do to a battery is to partially charge or discharge it. You normally (and I do this at least every couple of months) want to let the battery discharge completely. Then, charge it completely. Repeat this process at least two more times. Do this every couple / three months. This will give you the longest battery life: both in the lifespan of the battery and also in the power available in the battery.

---

### Post by Blauer Kuckuck on 2017-09-06
> **Autodave said:**
> Not that I know of.  Besides, why would you want to do that? That would only serve to shorten the battery's life. The worst thing you can do to a battery is to partially charge or discharge it. You normally (and I do this at least every couple of months) want to let the battery discharge completely. Then, charge it completely. Repeat this process at least two more times. Do this every couple / three months. This will give you the longest battery life: both in the lifespan of the battery and also in the power available in the battery.

Thank you for your response! I think that your recommendations concerning the use of batteries do not apply for lithium-ion batteries. As far as I know (source: [http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/](http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/) ), lithium-ion batteries have the longest lifetime if their charging cycles are always kept somewhere in between 20% and 80%.

---

### Post by Autodave on 2017-09-06
> **Blauer Kuckuck said:**
> Thank you for your response! I think that your recommendations concerning the use of batteries do not apply for lithium-ion batteries. As far as I know (source: [http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/](http://www.techrepublic.com/blog/five-apps/five-tips-for-extending-lithium-ion-battery-life/) ), lithium-ion batteries have the longest lifetime if their charging cycles are always kept somewhere in between 20% and 80%.

I realize that Nicads were/are different. But the article that you referred to still talks about the memory of the battery and recommends every 30 days a complete discharge. The difference in life expectancy between what I said and what the article stated is going to be very minimal. I do agree with the article about storing it at less than full charge or even 50% status. By storing, I mean for longer than a few days/weeks.

Realize that repetitive charging and discharging will wear the battery out quicker than just leaving it charged and doing what I recommended before. And trying to maintain it between 20 & 80% is going to wear you out! :-)

I have laptops with lithium-ion batteries that are over 8 years old and still doing quite well. Like new? No. But still OK for the hour or so when no AC power is available.

After having said all of that, I leave you with this: If you are talking about a laptop that has an easily replaceable battery (not a unit that requires major surgery), replacement batteries with new specs or even way better specs are very inexpensive now.

---

### Post by Autodave on 2017-09-08
Interesting thing just happened: I had ordered a replacement lithium-ion battery for one of my laptops. It arrived a few minutes ago and I did something that I rarely do: I read the paper that came with it! It recommends a full charge before storing the battery/laptop for an extended period. (Contrary to what your website suggested.)

---

### Post by efflandt on 2017-09-10
Because most people do not know that lithium batteries should not be left fully charged for long periods or left always plugged into AC power, chargers for them do not charge them up to the full 4.2 volts per cell, they top off at something less than that. Also the monitoring circuitry in laptop batteries to avoid over charging or discharging excessively may trickle the batteries down over time, which may be why they recommend fully charging them before storage. The main reason laptop manufacturers recommend using them on battery power periodically is to auto calibrate the battery meter of the OS (or battery circuitry?), so you can reliably determine how much battery time you have left.

RC modelers who use and learn about lithium polymer batteries (similar to lithium ion, but with soft case) know that rechargeable lithium batteries store best at 1/2 charge and their life would be shortened if left for long periods or time fully charged or fully discharged. But they have more complete control over the charging process and there is no internal circuitry in those batteries to drain them over time. So if flying electric aircraft, they will store the batteries at half charge, charge them fully before flying, then charge them half way after flying, only fully charging them if they are going to continue flying or fly again soon.

---

