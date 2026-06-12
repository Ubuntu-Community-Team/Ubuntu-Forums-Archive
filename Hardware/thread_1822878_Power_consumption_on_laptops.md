---
title: "Power consumption on laptops"
date: 2011-08-11
forum: Hardware
---

### Post by seicean on 2011-08-11
Hello

I realised in recent days that I get substantially high power consumption while running on battery power (screenshot attached).

When I was running W7, i got around 14-16 Wh, now I get around 22-23 Wh, which make a difference in battery life...

My screen is dimmed at max, wi-fi & bluetooth are turned off and the "spin hard drive off" is also ticked.

My conf:
Lenovo N500
Core 2 Duo 2.0 GHz
3Gb DDR2
nVidia GeForce 9300M
Sony Battery - 52.7Wh
250GB Samsung HDD

Any help is much appreciated...

---

### Post by aeronutt on 2011-08-11
What version of Ubuntu are you running, and what programs are run automatically at startup? But with that said, I'd expect it's your graphics card. I have an AMD discrete card, and with it on, I burn nearly 2x the power. W7 manages that card much better than Ubuntu.

---

### Post by matt_symes on 2011-08-11
Hi

Here's another one to check. What speed is your CPU running at ?

```
cat /proc/cpuinfo | grep -i "cpu mhz"
```

Have you analysed your system using powertop ?

```
sudo apt-get install powertop
```

Kind regards

---

### Post by seicean on 2011-08-11
> **aeronutt said:**
> What version of Ubuntu are you running, and what programs are run automatically at startup? But with that said, I'd expect it's your graphics card. I have an AMD discrete card, and with it on, I burn nearly 2x the power. W7 manages that card much better than Ubuntu.

I'm running Ubuntu 11.04 64bit. No programs running on startup, just the default ones... 

I'll install power top and check the nvidia control panel and post a screenshot ASAP... 

thanks for the response

---

### Post by ajgreeny on 2011-08-11
Install powertop then run ```
sudo powertop
``` in terminal.  It will help you to at least see what is using the power, and will offer keypresses to reduce wattage used.  Unfortunately the keypresses do not persist after a reboot, but when on battery they reduce the wattage used by my netbook from about 11 down to 9.7.

---

### Post by seicean on 2011-08-11
posted some screens with powertop in terminal and from the nvidia CP... ideas?

---

### Post by matt_symes on 2011-08-11
Hi

CPU looks fine. It is spending most of its time in state P3.

Have a look, as suggested, at your video hardware. Also, try the power saving tips powertop suggests (also as suggested).

Kind regards

---

### Post by seicean on 2011-08-11
> **matt_symes said:**
> Hi

CPU looks fine. It is spending most of its time in state P3.

Have a look, as suggested, at your video hardware. Also, try the power saving tips powertop suggests (also as suggested).

Kind regards

Thank You very much... I'll give it a try.

---

### Post by sanderd17 on 2011-08-11
I noticed a significant increase in battery time after I did what this post suggests: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

Don't know if it will help you though.

---

### Post by seicean on 2011-08-11
> **sanderd17 said:**
> I noticed a significant increase in battery time after I did what this post suggests: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

Don't know if it will help you though.

Thanks! I'll give it a try and post a result...

---

