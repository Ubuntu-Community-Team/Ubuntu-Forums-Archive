---
title: "Power consumption on a MacBookPro 10,1"
date: 2014-09-05
forum: Hardware
---

### Post by Elv13 on 2014-09-05
Hello,

I decided to install Ubuntu on my laptop (from Gentoo) mainly because I had issues tweaking power managment. I see some forum posts (1) saying the laptop should run on ~12-14 watts when using the Intel driver (the laptop also has an NVIDIA GPU), minimal brightness and ethernet adapter rather than WIFI. However, when echoing BAT0/power_now while on battery, I see a power usage of 22-26 watts. I ran powertop and applied all changes and see no major sources of wakeup.

In the end, I can't find why I use twice the power as other users of the same laptop. It has an Ivy Bridge i7 CPU, Boardcom Wifi (... I guess I should replace it with an Atheros, I hate Boardcom) an SSD and soldered on RAM. I have no other devices connected beside the ethernet adapter (< 1 watt, no LED). Any idea whats wrong?

OS: Ubuntu 14.04 stock, also tried with fluxbox, same results.

(1) [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)

---

