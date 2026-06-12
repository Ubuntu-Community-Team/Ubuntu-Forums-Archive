---
title: "Super optimize power consumption"
date: 2012-04-27
forum: Hardware
---

### Post by krypt0nite on 2012-04-27
Hey,
I have A Samsung 300E5z-S01IN laptop. running Core i3 2nd genertion with Nvidia Optimus (HD3100+520MX) on Intel Hm65 Chipset with intel series6 audio controller and centrino 100n wifi and realtek 8111 ethernet.

on windows 7 it consumes 8-14 watts with wifi on bluetooth off, powersave mode, minimum brightness,

on ubuntu 12.04 , consumption if up from 15W.  i mean more than 15Watts (15-21).

I want to lower the power consumption to that of windows . I want all possible optimisations


So far
I have limited cpufreq to 800Mhz/ powersaving mode
And WIFI tx to 4dBm

*I want to switch off soundcard/ethernet controller when not in use
*Its sandybridge and i aint waiting for Linux 3.4 to arrive .Ubuntu devs have backported RC6 state to this LTS release. Is it working fine?

#bug. using cpufreqd to lower consumption makes my logitech wireless mouse less responsive . it takes time to wake up. mayb usb polling is affected by low cpufreq ?
Please any inputs are welcome !

---

