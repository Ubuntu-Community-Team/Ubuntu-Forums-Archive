---
title: "Battery not charging above 80%"
date: 2012-09-15
forum: Hardware
---

### Post by cphus on 2012-09-15
Hello there,

I have a Lenovo laptop, 2yrs old now, and for some reason the battery started behaving peculiarly not charging above 80%. In the meantime I switched quite often the distribution I was using (I had Mint, Ubuntu, Crunchbang) and the battery used to last with each one about 2h-2h15m. I also have Windows 7 and I could get a little bit more with power saving activated - like 2h30+. 

RIght now I'm using Kubuntu 12.04. The battery is Li-ion. I browsed a bit the net and some people say that it might help discharging the battery below 5% then fully recharging it. I made this a few times but I can't notice any improvement. Also, it seems to be a hardware problem since neither Windows 7 can charge it above 80%.

Here are some outputs, if relevant:
```
$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         47520 mWh
last full capacity:      24550 mWh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mWh
design capacity low:     156 mWh
cycle count:              0
capacity granularity 1:  264 mWh
capacity granularity 2:  3780 mWh
model number:            PABAS024
serial number:           3658Q
battery type:            LION
OEM info:                LG
```

```
cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            12800 mW
remaining capacity:      18410 mWh
present voltage:         11404 mV

```

Any ideas what could I do?

---

