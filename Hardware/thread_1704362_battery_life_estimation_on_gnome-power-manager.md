---
title: "battery life estimation on gnome-power-manager"
date: 2011-03-10
forum: Hardware
---

### Post by changsijay on 2011-03-10
Hi, I am using Mint on macbook pro,
and gnome-power-manager works fine on official kernel (linux-image-2.6.35-27-generic-pae)
it can show estimated battery life.

But after I change kernel to my customized one.
It always show "under estimating..."
looks as here: [IMG]http://commondatastorage.googleapis.com/csj/temp/battery.png[/IMG]

I've checked lsmod, I have "battery" module loaded,
Other information as below:

cat /proc/acpi/battery/BAT0/state
```
present: yes
capacity state: ok
charging state: discharging
present rate: 14938 mW
remaining capacity: 35560 mWh
present voltage: 11447 mV
```


cat /proc/acpi/battery/BAT0/info
```
present: yes
design capacity: 57700 mWh
last full capacity: 56050 mWh
battery technology: rechargeable
design voltage: 10950 mV
design capacity warning: 250 mWh
design capacity low: 100 mWh
cycle count:	 0
capacity granularity 1: 10 mWh
capacity granularity 2: 10 mWh
model number: bq20z451SD3BADEF0123456789ABCDE
serial number: 
battery type: LIONz451SD3BADEF0123456789ABCDE
OEM info: SMPNz451SD3BADEF0123456789ABCDE
```


cat /sys/class/power_supply/BAT0/status
```
Discharging
```


my kernel 2.6.38-rc8 config is here
[http://commondatastorage.googleapis.com/csj/kernel%20config/config-2.6.38-rc8_macbookpro]("http://commondatastorage.googleapis.com/csj/kernel%20config/config-2.6.38-rc8_macbookpro")
Did I miss any config to cause this issue?

---

