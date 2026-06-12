---
title: "Ubuntu 8.10: Laptop Battery Discharge Accuracy"
date: 2008-11-20
forum: Hardware
---

### Post by kestal on 2008-11-20
Not sure if anyone has had or heard of this problem... I wouldn't have even noticed until one time, when turning on my laptop (in Ubuntu Intrepid), a notification at the bottom said that my total battery capacity was at 46% and that it might be damaged.

I figured that Ubuntu took more juice than when I was using Windoze (and it does), but never did I think that it would cause problems?

So I decided to do a full discharge. According to the battery meter, I had 1 hour to do a full discharge. Of course, thats an estimation.. but what I realized was that after that 1 hour and after my battery meter hit 0%, I had an extra 40 minutes of juice left before it actually just shut off...

Is there any way to Reset the battery meter so it just calculates the accuracy for the first time (from full charge to full discharge?) I just recently (re)installed Intrepid and the inaccuracy is still there. Or does it not work that way?

---

### Post by sdennie on 2008-11-20
That number is usually reported by the battery itself via the BIOS.  See if the values you see with the gnome power manager match the values you see with:

```

cat /proc/acpi/battery/*/info
cat /proc/acpi/battery/*/state

```

Specifically, look at the "remaining capacity", "design capacity" and "last full charge capacity" numbers.

---

### Post by mrufino1 on 2008-11-20
I am wondering if this is a recent bug form an update, because I was getting 4 hours plus on my extended battery (IBM t41) 2 days ago and suddenly it is "discharging" really fast. Th ebattery is only a few months old, so it should be fine, I will be watching with interest. I think there may have been an acpi update in the last batch?

---

### Post by mrufino1 on 2008-11-20
> **vor said:**
> That number is usually reported by the battery itself via the BIOS.  See if the values you see with the gnome power manager match the values you see with:

```

cat /proc/acpi/battery/*/info
cat /proc/acpi/battery/*/state

```

Specifically, look at the "remaining capacity", "design capacity" and "last full charge capacity" numbers.

I just ran that and they do look different, but I have to leave in a hurry, I'll try again later and do the math.

---

### Post by kestal on 2008-11-20
a bit more info actually,

I fully discharged it (+40-ish min), fully charge, then discharged again(+40-ish min) and now my capacity is at 69%. My last charge capacity went from about 30000 mWh (I wrote it down) to just above 45000 mWh. 

My Design capacity is at 69120 mWh. my last charge/charge remaining (the first time I tried) was just below 30000. I just find it weird that my laptop battery meter sits at 0% for an extra 40 minutes... but would that mean its charging beyond (well, what now is the current capacity of) 45000 mWh and just not counting it?

So aside from milking a full discharge (and then some), is there nothing I can do about this?

Edit: Just double-checked my bios. There is absolutely no information visible thats related to battery. (unfortunetely).

---

### Post by kestal on 2008-11-20
Yeah, same problem happening now. I am at 0%. my current charge/charge left is at 0 mWh. Its been like that for 15 minutes. Though, next time I charge I hope to see an improvement in the capacity. (Hope). My battery used to last only 50 minutes, but now its almost 2 hours... Not sure if this is normal or not, or if I am overkilling my battery.... or if its just something that happened while i was on Windows... (the charge was pretty bad then too, I think).

---

### Post by mrufino1 on 2008-11-21
Well, I hit 0% yesterday and then it shut down...I hope my battery didn't decide to give out. I'll be watchign closely today- I understand with lithium batteries you are supposed to completely discharge them once in a while.

---

### Post by mrufino1 on 2008-11-21
Sorry to replay to my own post, but in case anyone is subscribed I thought an update would be good. So it seems my battery is back on track- my laptop has been running on battery for about 3 hours and is reporting 1 hour left, so I must have needed to deplete and recharge with the computer off. I'll have to remember to do that once a month. I also set my battery conservation settings conservatively again (not that that is what was making it last only an hour), dimming the screen, etc.

---

### Post by kestal on 2008-11-21
Yeah.. im not sure what to make out of my experience.

My overall battery capacity was 46% compared to the design capacity.. then 69.. now 75. I keep discharging it until it turns off, which is usually 15-20 minutes after it hits 0% battery in the battery meter. It went from 50 minutes (on battery meter) to 2 hours and 20 minutes.

---

