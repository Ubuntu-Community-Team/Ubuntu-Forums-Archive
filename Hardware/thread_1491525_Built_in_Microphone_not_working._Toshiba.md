---
title: "Built in Microphone not working. Toshiba"
date: 2010-05-23
forum: Hardware
---

### Post by BorgCymru on 2010-05-23
Toshi9ba Satellite L4500-11V

Ubunto 10.04

Can't seem to find any way of getting the built in mic working . Any clues where to start looking ?

Thanks

---

### Post by primatology on 2010-06-24
I had the same issue with a Toshiba Satellite M305D--couldn't get either the internal or an external microphone to work. I inadvertently stumbled upon the solution when trying to convert from ALSA to OSS4. I'm not sure why this works, but using soundcheck's [ALSA upgrade script](http://ubuntuforums.org/showthread.php?t=1046137) fixed everything.

Let me know if this works for you. (Most of the other solutions I've found, such as changing configuration files, don't seem to help with Toshiba laptops.)

---

