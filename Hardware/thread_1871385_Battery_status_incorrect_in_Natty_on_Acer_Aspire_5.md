---
title: "Battery status incorrect in Natty on Acer Aspire 5551 laptop"
date: 2011-10-28
forum: Hardware
---

### Post by ShaneIreland on 2011-10-28
For the past few months, I've been having problems with my laptop's battery.

No matter how long I leave it plugged in, Ubuntu only shows 5-15 minutes remaining, or 5-20% charge. If I don't plug it in quickly, it will suspend/hibernate.

The laptop was purchased in October 2010 (one year ago).

I rarely use Windows 7 on my laptop, but when I do there are no battery problems.

[FONT="Courier New"]less /proc/acpi/battery/BAT1/info[/FONT] gives:
> present:                 yes
design capacity:         4400 mAh
last full capacity:      4304 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 220 mAh
design capacity low:     132 mAh
cycle count:              0
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            AS10D31
serial number:           0099
battery type:            Lion
OEM info:                Sanyo 


[FONT="Courier New"]upower --dump[/FONT] gives (please note I'm on AC power with battery level at 7% while executing this):
> Device: /org/freedesktop/UPower/devices/line_power_ACAD
  native-path:          /sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD
  power supply:         yes
  updated:              Sat Oct 29 00:11:01 2011 (3099 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT1
  vendor:               Sanyo
  model:                AS10D31
  serial:               0099
  power supply:         yes
  updated:              Sat Oct 29 01:02:15 2011 (25 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              3.2616 Wh
    energy-empty:        0 Wh
    energy-full:         46.4832 Wh
    energy-full-design:  47.52 Wh
    energy-rate:         0 W
    voltage:             12.28 V
    percentage:          7.01673%
    capacity:            97.8182%
    technology:          lithium-ion

Daemon:
  daemon-version:  0.9.9
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  yes
  is-docked:       no


I'm now using a "switching mode regulated power supply" power block, but use with the original manufacturer-supplied power block had the same problems.
Let me know if you need more information.

Thanks in advance.

---

### Post by ShaneIreland on 2011-11-01
Great news!

I just found out today that my laptop is behaving much more.

It gave the laptop battery as 45% with about an hour left.

Here's what I tried:
I used the computer as normal for a while (about an hour), not plugged in, ignoring all the warnings.
In the terminal: acpi_apic_instance=2

I'm not sure if it's one or these, or something else that fixed the situation.

I hope someone can explain what happened to me, file a bug report, etc.

---

