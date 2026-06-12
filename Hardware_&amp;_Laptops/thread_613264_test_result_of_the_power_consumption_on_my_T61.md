---
title: "test result of the power consumption on my T61"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by bittergourd on 2007-11-14
just for curiosity,  i tested the power consumption under 710 on my laptop and compared with xp.  here is the conditions and results:

hardware: thinkpad t61 (14&#8220; 1024*768) + T7300 + X3100 graphics + 2GB ram

gutsy-
tested with powertop.  wireless off, lowest lcd backlight, hdd off, lan unpluged, dri disabled, laptop_mode on, mouse not moving.

cpu stays mostly (>99%) in its C3 (maybe C4) mode, and wakes up every 100 ms.  the minimum power is

[SIZE="5"]**11.0 W**[/SIZE]

i didn't do everything that i could have done according to lesswatts.org, but i don't think there is much space to squeeze further than what i already did.

xp-
tested with the power management software that came with thinkpad.  wireless off, lowest lcd backlight.  note that the hdd is **ON**

the mininum (averaged) power is
[SIZE="5"]**7.5 W**[/SIZE]

i don't have vista.  presumably it should do a slightly better job than XP.

given the fact that my battery is 55 W*hr, i got 5 hr vs 7.3 hr battery time (not really functioning at those low energy states tho)

it seems that ubuntu still has a long way to go for laptops.

- yi

---

### Post by lamborghiniwang on 2007-11-15
My T61p also draw more power under gutsy than it does under xp.
Did you apply the backlight-fix patch? From what I can tell from [ the second figure]("http://www.lesswatts.org/results/mobile/"), it seems the backlight bug eats almost 3watt of power.

---

### Post by John Jason Jordan on 2007-11-16
> **lamborghiniwang said:**
> My T61p also draw more power under gutsy than it does under xp.
Did you apply the backlight-fix patch? From what I can tell from [ the second figure]("http://www.lesswatts.org/results/mobile/"), it seems the backlight bug eats almost 3watt of power.
What is the backlight-fix patch?

---

### Post by bittergourd on 2007-11-17
i didn't install the patch, but the backlight control seems working:  when i reduce the brightness, the power goes down accordingly.

> **lamborghiniwang said:**
> My T61p also draw more power under gutsy than it does under xp.
Did you apply the backlight-fix patch? From what I can tell from [ the second figure]("http://www.lesswatts.org/results/mobile/"), it seems the backlight bug eats almost 3watt of power.

---

