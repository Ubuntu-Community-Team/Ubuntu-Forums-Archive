---
title: "HP2000-2b19wm Laptop: Completely Disable Frequency Scaling?"
date: 2014-02-23
forum: Hardware
---

### Post by Krovas on 2014-02-23
HP2000-2b19wm Laptop
Precise Pangolin 12.04.3 LTS x64

I'm trying to get my cheap laptop to run flat-out all the time. When both cores are pegged, and k10temp@c3 climbs above 55.0 centigrade (as reported by GKrellm), the clock-speed throttles back from 1.3 to 1.11. Not much, admittedly, but a little annoying. This rig needs all the power it can muster, and I'm really not concerned with its very-long term survival, anyway. Barring a complete scaling disable, how might I at-least change the temperature threshold to something more reasonable (65 C, say)? Any feedback constructive to either of these ends would be appreciated. Let m know if you need any additional data. Thank you kindly.

---

### Post by Krovas on 2014-02-24
*bump*


Anyone. Buehler?

---

### Post by Yellow Pasque on 2014-02-24
This works on my desktop, bu I don't know so much about laptops:
```
sudo cpufreq-set -g performance
```

---

### Post by Krovas on 2014-02-25
> **Temüjin said:**
> This works on my desktop, bu I don't know so much about laptops:
```
sudo cpufreq-set -g performance
```


No joy. The cores run at 1.30 until the above conditions are met, and drop back down to 1.11 for the duration. 

I can't find a BIOS setting for this. Would it be handled by something at the kernel level, some higher level software, or is it likely a hardware decision that I can't change? This is uncharted territory for me.

---

### Post by Krovas on 2014-03-01
Okay, the short solution.

/etc/cpufreqd.conf: change...


```

##
# Special Rules
##
# CPU Too hot!
[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

```


...acpi_temperature=***55***-100 to 65-100, or whatever lower end you're comfortable with. Seems a more elegant (and ultimately safer) solution than merely blacklisting the kernel module (which may not be so easily done as simply blacklisting *acpi-cpufreq*, anyway, I gather). With both cores balls-to-the-wall (courtesy of Prime95 x64: [http://www.mersenne.org/freesoft/](http://www.mersenne.org/freesoft/)), my lappy is hard-pressed to hit 63C. Of course YMMV; if you end up smoking something, it's not my fault. Use this knowledge wisely.

---

