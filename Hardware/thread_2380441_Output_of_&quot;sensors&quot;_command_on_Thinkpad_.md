---
title: "Output of &quot;sensors&quot; command on Thinkpad seems odd"
date: 2017-12-17
forum: Hardware
---

### Post by mechsectech on 2017-12-17
I recently noticed that the fan on my Thinkpad t470 doesn't appear to be running at all in Ubuntu. 
When I run the command "sensors" the output is as follows:

```
iwlwifi-virtual-0
Adapter: Virtual device
temp1:        +32.0°C  


pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +38.0°C  


acpitz-virtual-0
Adapter: Virtual device
temp1:        +42.0°C  (crit = +128.0°C)


thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM


coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +40.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +39.0°C  (high = +100.0°C, crit = +100.0°C)
```

My question is should the temperature value for **coretemp-isa-0000** be the same for "**high**" and "**crit**" or should one be lower than the other?

---

### Post by DuckHook on 2017-12-17
Welcome to the forums, mechsectech.

> **mechsectech said:**
> I recently noticed that the fan on my Thinkpad t470 doesn't appear to be running at all in Ubuntu&#8230;
That's because all of your core temperatures are enviously cool. If Ubuntu judges that it doesn't need cooling, then it won't call on the fans.
> &#8230;should the temperature value for **coretemp-isa-0000** be the same for "**high**" and "**crit**" or should one be lower than the other?
If you want to be really persnickety about it, then *"crit"* should be higher than *"high"*, but since your operating temps are so low anyway, is this really a concern? I wouldn't be the least bit worried about it.

---

### Post by mechsectech on 2017-12-17
Ahh thank you so much for the reply, I had a feeling I was worrying about nothing. 
Even still, I already installed **Thinkfan** and set the fans to turn on for very low temperatures just in case. 

> ...then *"crit"* should be higher than *"high"*, but since your operating temps are so low anyway, is this really a concern?

Probably not, but how would I go about making that change? (just for future reference).

---

### Post by DuckHook on 2017-12-17
> **mechsectech said:**
> Even still, I already installed **Thinkfan** and set the fans to turn on for very low temperatures just in case.
When you want the fans turning on is your choice, but I would note the following:

[LIST=1]
[*]Fans are mechanical devices and the less used (unless necessary, of course) the longer they last.
[*]39° is only 2° higher than human body temperature. So, your cores and GPUs would only feel slightly warm to your touch—*without fan!* That's already pretty impressive efficiency. For comparison, my old laptops commonly run at 48°C for CPU and 65°C for GPU. And even at those temps, the fan rarely comes on.
[*]Fans can be noisy (depending on fan quality and speed).
[/LIST]
> Probably not, but how would I go about making that change? (just for future reference).
You may end up wishing you'd never asked this question.  :P

The process is quite obscure and arcane. This is because lm-sensors is no longer maintained, was pretty obscure to start with, is undocumented and the way that various MOBO sensors report their temps is ridiculous. The combined effect is like pulling teeth and deciphering the process is not for the faint of heart. The main resources I used were:

[https://lvogdt.wordpress.com/2013/02/19/short-lm_sensors-howto/](https://lvogdt.wordpress.com/2013/02/19/short-lm_sensors-howto/)
[http://ubuntuforums.org/showthread.php?t=1675550&page=6](http://ubuntuforums.org/showthread.php?t=1675550&page=6)
[https://github.com/groeck/nct6775](https://github.com/groeck/nct6775)

The general approach involves creating a new file in */etc/sensors.d* that lm-sensors will read every time it launches. This file uses offsets to adjust lm-sensors' readings, conversion factors, and default values. I had to design such a file because lm-sensors kept raising alarms on readings that were, in fact, perfectly fine. In all candour, generating the file was an exercise out of Hogworts school of magic, but since I was relying on lm-sensors for my system alerts, the wonky readings could not be ignored. I believe that I spent a week of evenings researching, experimenting, editing the file, booting and rebooting.

If you are up to this, then I doff my hat to you. If you prefer to just ignore these silly misreadings, then you are merely in the company of the sane.

---

### Post by Yellow Pasque on 2017-12-18
> **DuckHook said:**
> This is because lm-sensors is no longer maintained

lm-sensors lost their server, so there are a lot of broken links floating on the web, but lm-sensors userspace is still maintained on github: [https://github.com/groeck/lm-sensors/commits/master](https://github.com/groeck/lm-sensors/commits/master)
And, of course, work for supporting new sensors continues in the kernel: [https://github.com/torvalds/linux/commits/master/drivers/hwmon](https://github.com/torvalds/linux/commits/master/drivers/hwmon)

---

### Post by DuckHook on 2017-12-18
Appreciate the links, Temüjin.

---

