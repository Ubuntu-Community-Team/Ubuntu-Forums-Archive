---
title: "Weird Intermittent Display Problem with Lubuntu 18.04 on Thinkpad T420s"
date: 2020-02-13
forum: Hardware
---

### Post by wjbmd48 on 2020-02-13
Hi:

I came into a T420s with an I7 2.8Ghz processor. I swapped into it a fully functioning SSD drive from a T420s which has a I5 2.5Ghz processor, and maybe a different display?

Everything works well *except* that the display intermittently fires up as 1024x768, with loss of horizontal exposure. This doesn't happen all the time, and I can fix it by, oddly enough, shutting it down, removing the AC power and battery, waiting 5-10 minutes, and then firing it up again.

I suspect I'm looking at a fresh install to correct this; is there any way to trouble-shoot this short of a fresh install?

Thanks!!

Bill

---

### Post by wjbmd48 on 2020-02-13
Sorry, I forgot to mention that the normal display is 1600x900, which is what I want it to boot to, and does so most of the time. The 768x1024 display comes up most reliably with a reboot.


Bill

---

### Post by EuclideanCoffee on 2020-02-13
I suspect you're having power issues. Please check your dmesg for errors related to power.

dmesg | grep 'Error'

or 

dmesg | grep 'error'

---

### Post by wjbmd48 on 2020-02-13
OK, thanks!

here's what i get with desmg | grep 'error':


[    1.860558] mmc0: error -110 whilst initialising SD card
[    2.056028] mmc0: error -110 whilst initialising SD card
[    2.220335] mmc0: error -110 whilst initialising SD card
[    2.392286] mmc0: error -110 whilst initialising SD card
[   16.074054] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro

i don't know how to interpret that, interestingly, tho, my inserted SD card wasn't showing, but was fine when i ejected/reinserted it. i'm also not sure what's meant by "power issues."

bill

---

