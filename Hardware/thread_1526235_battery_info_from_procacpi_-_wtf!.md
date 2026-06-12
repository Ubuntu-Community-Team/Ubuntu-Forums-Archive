---
title: "battery info from /proc/acpi - wtf?!"
date: 2010-07-07
forum: Hardware
---

### Post by morgonhed on 2010-07-07
Hi,

I just got a new battery from ebay for my Thinkpad X30 that is supposed to have a capacity of 5200 mAh which it does not seem to have.

Before I complain I wanted to double-check that I understand this properly ...

Here is what I get from /proc/acpi in Lucid:


cat /proc/acpi/battery/BAT0/info 

present:                 yes
design capacity:         43200 mWh
last full capacity:      43200 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 2160 mWh
design capacity low:     432 mWh
capacity granularity 1:  1 mWh
capacity granularity 2:  1 mWh
model number:            IBM-02K6620
serial number:             354
battery type:            LION
OEM info:                Panasonic


Has the file-format canged here so that that capacity is no longer reported in mAh, but in mWh?

And am I right that if I want to have the capacity in mAh I need to calculate

my capacity =  43200 mWh / 10800 mV = 43200 mWh / 10.8 V = 4000 mAh

Is that the way to do it?

Many thanks!

---

