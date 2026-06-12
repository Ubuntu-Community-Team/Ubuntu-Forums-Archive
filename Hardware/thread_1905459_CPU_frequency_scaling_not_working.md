---
title: "CPU frequency scaling not working"
date: 2012-01-06
forum: Hardware
---

### Post by PARO on 2012-01-06
[long story] hello. i had been really disappointed by the battery life my netbook had gotten under ubuntu, and so i switched to meego, and i was happy :), using ubuntu only for things that only ubuntu could do. however, recent news about meego's end i thought i'd try out a lighter debian distro (#!) and found that burns hotter and shorter then meego also. which began my quest in testing energy consumption in a number of different oses. I found that debian based distros used roughly the same amount of energy (ubuntu with unity slightly more,but was the only one that would drop when i killed wifi), puppy was a little less, but still quite a bit more than meego. android-x86 was about the same as debian distros, and windows 7 starter ed. used about 30% less energy when idle than any of them! (except meego, which was roughly the same as win7... which actually makes sense since the lowest CPU setting is about 30% of max CPU level) but that really surprised me![/long story]

[crux] i realized that these distros were probably not throttling my cpu properly. while they say they are working and the terminal reads things like: "Current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:26.87%, 1.33 GHz:2.28%, 1000 MHz:70.85%  (14321)"
and when altered reads correctly the changes "performance" etc. and i found there was 0 change in energy usage despite the changes made to the governor and frequency. i have a standard atom n450 processor, so i'd imagine a LOT of people should have this problem, but searching on the web i found a lot of people content with the terminal read-out as verification that it was working. and many others complaining that ubuntu eats their battery far faster than windows, but with no explanation why.[/crux]

[question(s)] is this a bug? or has anyone else actually tested their setup to verify that it is actually working, and found it does for them? is there something necessary to do that's strangely absent in debian distros (or most linux distros in general)?[question(s)]

---

### Post by 2F4U on 2012-01-07
There is a kernel bug concerning power management detected by Phoronix and others. For a start read through

[http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=OTg2Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg2Mg)
[http://phoronix.com/forums/showthread.php?59524-Linux-3-1-Kernel-Draws-More-Power-With-Another-Regression](http://phoronix.com/forums/showthread.php?59524-Linux-3-1-Kernel-Draws-More-Power-With-Another-Regression)
[http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1)

There are several kernel options available that can significantly reduce power consumption, mainly usb auto suspend, pci power management and graphics card power management.
Some of these options depend on what chipset you are using. Using proprietary nVidia or AMD drivers may help to reduce power consumption since the power management is better in those graphics drivers.

---

### Post by PARO on 2012-01-07
ah, so i checked in meego 1.1 and the kernel i had been using must've been 2.6.35 kernel and so not experienced the "power regression" that they say began with 2.6.38+. well back to meego 1.1 for now i guess.. thanks for the info.

---

### Post by PARO on 2012-01-13
more to it... i've checked ubuntu with kernel 2.6.35 and still cpu throttling does not effect power consumption, however meego seems to save about 20% idle with the same kernel and windows 7 saves over 30%. so it seems there is more to the story. can anyone confirm that cpu throttling works for them (using a power meter, not a terminal saying it is)? anyone know why this might not be working on a very typical netbook atom n450 processor?

---

