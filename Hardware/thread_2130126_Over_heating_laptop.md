---
title: "Over heating laptop"
date: 2013-03-28
forum: Hardware
---

### Post by blackadam on 2013-03-28
I recently dual booted my laptop with win 7 ultimate and ubuntu 12.04.  i noticed it started to over heat on me for unknown reason really it had been working fine with just windows and after a few weeks i notice that when once i chose to boot to ubuntu the fan stops working and i really can't spend more than 5-10min in ubuntu before i have to shut it down and let it cool off  I'm using an Acer Aspire 7720. Any ideas on how to verify if its the fan itself taking a poop or if i'm suppose to install a driver for the fan or something

---

### Post by spacesamurai on 2013-03-28
To ge the status/information for your fans, lm_sensors should do the trick.

Since this looks to only be occurring only on the Ubuntu install, I would start looking at the logs/modules you have installed to get further insight.

---

### Post by Mark Phelps on 2013-03-29
You could try using Jupiter: [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

There are no drivers for fans.

---

