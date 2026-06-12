---
title: "No Battery Stats"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by Didjit on 2006-06-25
Running an HP Omnibook 6100.  I'm getting 0 battery stats.

I see: Jun 25 08:11:23 localhost battery-stats-collector[4170]: apm_read failed with error code 1 

logged in the syslog.

Any suggestions??


If it helps, here is the output of lshal | grep battery

  battery.charge_level.rate = 0  (0x0)  (int)
  battery.charge_level.last_full = 64883200  (0x3de0a00)  (int)
  battery.charge_level.current = 0  (0x0)  (int)
  battery.voltage.current = 0  (0x0)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.current = 0  (0x0)  (int)
  battery.charge_level.capacity_state = 'ok'  (string)
  battery.rechargeable.is_discharging = false  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.is_rechargeable = true  (bool)
  battery.charge_level.unit = 'mWh'  (string)
  battery.charge_level.granularity_2 = 473600  (0x73a00)  (int)
  battery.charge_level.granularity_1 = 473600  (0x73a00)  (int)
  battery.charge_level.low = 2960000  (0x2d2a80)  (int)
  battery.charge_level.warning = 4440000  (0x43bfc0)  (int)
  battery.charge_level.design = 65120000  (0x3e1a700)  (int)
  battery.voltage.design = 14800  (0x39d0)  (int)
  battery.voltage.unit = 'mV'  (string)
  battery.reporting.granularity_2 = 32  (0x20)  (int)
  battery.reporting.granularity_1 = 32  (0x20)  (int)
  battery.reporting.low = 200  (0xc8)  (int)
  battery.reporting.warning = 300  (0x12c)  (int)
  battery.reporting.design = 4400  (0x1130)  (int)
  battery.reporting.last_full = 4384  (0x1120)  (int)
  battery.reporting.unit = 'mAh'  (string)
  battery.technology = 'LION'  (string)
  battery.serial = '633'  (string)
  battery.model = 'R09A$'  (string)
  battery.vendor = 'CHIN'  (string)
  battery.present = true  (bool)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  battery.type = 'primary'  (string)
  linux.acpi_path = '/proc/acpi/battery/BAT1'  (string)
  battery.present = false  (bool)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  battery.type = 'primary'  (string)
  linux.acpi_path = '/proc/acpi/battery/BAT2'  (string)


Tx

Didjit

---

