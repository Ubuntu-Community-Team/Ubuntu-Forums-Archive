---
title: "Acer AspireOne D250 Wrong CPU Clock"
date: 2009-07-01
forum: Hardware
---

### Post by tiger1986sg on 2009-07-01
Hi guys,

I've got everything to work on my Acer Aspire One D250 (Atom N280 CPU) except one thing. This CPU is supposed to be 1.66GHz however I'm only getting 1.33GHz.

Looking at /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies I only find three options:
1.33GHz
1.07GHz
800MHz

Verified it is not hardware problem. With Windows XP it hits 1.66GHz under "Always On".
Have spent over 2 days to google around and try to solve things myself. No hope at all.

I've tried kernel 2.6.30, backport modules too btw.. None works :( I'm getting frustrated now.

---

### Post by suomaf on 2009-07-04
Hello Tiger,

When you say you got everything working, do you include the cpu fan and wifi LED? If yes, can you share how you did it? 

Sorry I am no help with the CPU frequency, I have a D250 but I have not really looked at the cpu frequency.

Cheers

Suo

---

### Post by SnappyU on 2009-07-09
You are not alone.  I've a prob with the N280 on my MSI Wind as well ... :(
[http://ubuntuforums.org/showthread.php?t=1209082&highlight=n280](http://ubuntuforums.org/showthread.php?t=1209082&highlight=n280)

---

### Post by SnappyU on 2009-07-19
*bump*

---

### Post by Ultim8Fury on 2009-07-20
Not going to be a big help to you I'm afraid but my NB200 has an N280 processor in it and it reports 
 
1000mhz
1333mhz and 
1666mhz 
 
( figures may not be 100% accurate but the machine is at home and I'm not. So I doing it from memory, it's close enough though) 
 
It seems to happily switch between the various frequencies although it's almost always 1ghz or 1.6ghz . 
 
Like I said not a huge help, but it does at least show that Jaunty is capable of supporting the N280

---

### Post by ringe on 2009-09-01
Report your issues at [https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858)

---

