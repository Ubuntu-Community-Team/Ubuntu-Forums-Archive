---
title: "Battery icon disappears after resume from suspend"
date: 2009-11-08
forum: Hardware
---

### Post by vaibhav on 2009-11-08
I have a Compaq CQ40 laptop. After resuming from suspend, the battery icon disappears. The only way to make it reappear it seems is to restart Ubuntu karmic.

I did a diff of lshal before and after suspend. I find that the battery entry is not present in the one after suspend.

Please help!

$ diff lshal-before lshal-after
2c2
< Dumping 143 device(s) from the Global Device List:
---
> Dumping 142 device(s) from the Global Device List:
335,369d334
< udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
<   battery.charge_level.current = 42681  (0xa6b9)  (int)
<   battery.charge_level.design = 47520  (0xb9a0)  (int)
<   battery.charge_level.last_full = 47271  (0xb8a7)  (int)
<   battery.charge_level.percentage = 90  (0x5a)  (int)
<   battery.charge_level.rate = 0  (0x0)  (int)
<   battery.is_rechargeable = true  (bool)
<   battery.model = 'Primary'  (string)
<   battery.present = true  (bool)
<   battery.rechargeable.is_charging = true  (bool)
<   battery.rechargeable.is_discharging = false  (bool)
<   battery.remaining_time = 983  (0x3d7)  (int)
<   battery.reporting.current = 3952  (0xf70)  (int)
<   battery.reporting.design = 4400  (0x1130)  (int)
<   battery.reporting.last_full = 4377  (0x1119)  (int)
<   battery.reporting.rate = 0  (0x0)  (int)
<   battery.reporting.technology = 'Li-ion'  (string)
<   battery.reporting.unit = 'mAh'  (string)
<   battery.serial = ''  (string)
<   battery.technology = 'lithium-ion'  (string)
<   battery.type = 'primary'  (string)
<   battery.vendor = 'Hewlett-Packard'  (string)
<   battery.voltage.current = 12559  (0x310f)  (int)
<   battery.voltage.design = 10800  (0x2a30)  (int)
<   battery.voltage.unit = 'mV'  (string)
<   info.capabilities = {'battery'} (string list)
<   info.category = 'battery'  (string)
<   info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
<   info.product = 'Primary'  (string)
<   info.subsystem = 'power_supply'  (string)
<   info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'  (string)
<   linux.hotplug_type = 2  (0x2)  (int)
<   linux.subsystem = 'power_supply'  (string)
<   linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0'  (string)
< 
2964c2929
< Dumped 143 device(s) from the Global Device List.
---
> Dumped 142 device(s) from the Global Device List.

---

