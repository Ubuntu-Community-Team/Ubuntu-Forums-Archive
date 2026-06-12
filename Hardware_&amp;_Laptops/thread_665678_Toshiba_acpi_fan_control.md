---
title: "Toshiba_acpi fan control"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by iaha on 2008-01-12
Hi,

I've been having trouble with the fan on my Toshiba Satellite R25-S3503.
Since I've installed Ubuntu, it doesn't seem to have the fan come on at all.
A bit of a worry really.

I'm using the toshiba_acpi driver, and I was able to force on the fan, but it doesn't
seen to do anything. I'm checking my temp on the sytem by reading the /proc/acpi/thermal_zone/THRM/temperature file, using the hddtemp command to
read the hard drive temperature, and gkrellm to keep track of everything all the time.

I'm getting worry because the temp is hi all the time, and the fan doesn't turn on
at all, is there some one that can help me to speed up the fan or truly turn it on.

Thanks

---

### Post by santaslittlehelper on 2008-01-12
Hi

If this is a known problem or specific to you're laptop I don't know, but I would be worried to.
Maybe you could try using lm-sensors to get a better idea of what's going on.

You can follow these two howto's, make sure to read though them first, they can be slightly confusion, in my opinion anyway.

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=42737](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=42737)

Hope it might be useful and do be careful.

---

### Post by iaha on 2008-01-13
Thank you for your idea, I'm already using lm-sensors althoughI think something is not working write,
but I did the sensors-detect and the output of sensors command is:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (crit = +85.0°C) 

it doesn't mention any fan or any thing else, this is all it shows.
it mention that the cpu is at that temp but the THRM shows more than 67° C
and the hddtemp more than 50° C, I know is probably below critic temp, but with
windows is cooler, and that a big deal talking about a table pc..
appreciate any help...thanks

---

### Post by santaslittlehelper on 2008-01-13
Hi

Did some goggle, seems you already did, but ill post it anyway just in case.
[http://www.lm-sensors.org/ticket/2274](http://www.lm-sensors.org/ticket/2274)
[http://lists.lm-sensors.org/pipermail/lm-sensors/2007-October/021736.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2007-October/021736.html)

Some more goggle, this looked kind of interesting if the module supports you're model. Might be a long shot from reading here, in terms limited support. 
[http://omnibook.sourceforge.net/doku.php?id=readme#features_list](http://omnibook.sourceforge.net/doku.php?id=readme#features_list)
[http://omnibook.sourceforge.net/doku.php](http://omnibook.sourceforge.net/doku.php)
[http://ubuntuforums.org/showthread.php?t=561523](http://ubuntuforums.org/showthread.php?t=561523)

Then there's dust - probably not so much. ;)
[http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/11/dead-laptop-fan/](http://www.asklaptopfreak.com/laptop-notebook-help/2006/07/11/dead-laptop-fan/)

Lastly, maybe you should submit a bug report? This is a few I found sounding similar.
[https://bugs.launchpad.net/ubuntu/+bug/152988](https://bugs.launchpad.net/ubuntu/+bug/152988)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93241](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93241)

I at least was not really able to find a hole lot on you're specific model in terms of support under Linux.
But my own experience with various laptops are that sometimes very cool stuff happens so maybe a bug report would be the way to go.

I am fresh out of links hope you find some useful.

---

