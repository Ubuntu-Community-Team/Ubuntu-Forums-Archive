---
title: "Lucid: should I install laptop-mode-tools ?"
date: 2010-06-20
forum: Hardware
---

### Post by quini on 2010-06-20
Hi!

I'm using Ubuntu Lucid 64 bit on a Sony TT laptop.  I've already configured it through power manager, so it now:

-reduces the screen brightness when on battery
-reduces even more the screen brightness when on battery & idle
-stops hard disk when idle

But there are 3 features I'm missing from 9.10:

1. my Intel 5100 wireless card shows "Power Management:off" (it uses the iwlagn module)
2. both CPU cores are using the ondemand governor; I'd prefer them to use the powersave or conservative governors
3. I used to use laptop-mode to run a script when changing to battery or AC, as I can turn on/off the bluetooth and 3G hardware.  10.04 doesn't even have a /etc/rc.local directory to use instead (I guess I can just create it, but I'm not sure)

AFAIK, laptop-mode-tools was installed by default until 9.10, and could manage all 3 features.  Should I install it, or is it's been removed because it may conflict with the actual power management gnome application??

TIA  ;)

---

### Post by maestrobwh1 on 2010-07-14
I would also like an answer to this question...

---

### Post by Meizirkki on 2010-07-24
> **quini said:**
> Hi!

I'm using Ubuntu Lucid 64 bit on a Sony TT laptop.  I've already configured it through power manager, so it now:

-reduces the screen brightness when on battery
-reduces even more the screen brightness when on battery & idle
-stops hard disk when idle

But there are 3 features I'm missing from 9.10:

1. my Intel 5100 wireless card shows "Power Management:off" (it uses the iwlagn module)
2. both CPU cores are using the ondemand governor; I'd prefer them to use the powersave or conservative governors
3. I used to use laptop-mode to run a script when changing to battery or AC, as I can turn on/off the bluetooth and 3G hardware.  10.04 doesn't even have a /etc/rc.local directory to use instead (I guess I can just create it, but I'm not sure)

AFAIK, laptop-mode-tools was installed by default until 9.10, and could manage all 3 features.  Should I install it, or is it's been removed because it may conflict with the actual power management gnome application??

TIA  ;)

Afaik laptop mode tools in no more used because it is conlicting with some other powersaving features. Instead many of it's features are merged in other applications.

My screen dims automatically, thanks to PowerDevil (KDE). HDD also spins down all the time when not used. I have no idea what does it but the feature exists.

1. Wlan indeed eats a lot of power, but i'm not familiar with the powersaving methods as I'm not using wlan on normal use.
2. Ondemand governor is actually very good IMO. It raises the frequency only when necessary, even though that means taking temporarily more power, the overall consumption may be lower because the tasks are faster done and CPU can go idle. PowerDevil also handles this for me and I can set the governor to whatever I want.
3. Also handled by PowerDevil in my case. And you can use rc.local in 10.04 too.

---

