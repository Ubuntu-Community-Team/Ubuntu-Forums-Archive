---
title: "Lenovo Ideapad S10-3 temperature &amp; fan"
date: 2011-04-23
forum: Hardware
---

### Post by dimoftheyard on 2011-04-23
Hello there,

I am running Xubuntu 10.10 on an Ideapad S10-3. Everything is working fine, but the computer is quite warm. The output of sensors was

```

$ sensors
 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +53.0°C  (crit = +100.0°C)

```when I had a terminal and firefox running, but no websites with flash displayed. After the laptop slept for some hours the temperature was down to

```


acpitz-virtual-0
Adapter: Virtual device
temp1:       +35.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (crit = +100.0°C)    


```but within minutes it grew to a similiar level, although I was only typing text.

The temperature is the same running from battery and on AC. The only difference is that when the power cord is plugged in the fan is running non-stop (and is beeing quite loud doing that), but that does not seem to change the temperature at all.

I did some google search, but did not find any explanation. Is 60°C normal for a netbook? My bigger laptop is running on ~40°C with normal usage. Or is there a way to bring that temperature down, and maybe make the fan stop occasionally?

Thank you!

---

