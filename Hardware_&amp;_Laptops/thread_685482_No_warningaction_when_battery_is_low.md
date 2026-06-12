---
title: "No warning/action when battery is low"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by ronaldv on 2008-02-02
Hi

I have Ubuntu 7.10 installed on a Sony Viao vgn-fz21m (kernel 2.6.22-14-generic). It is running fine.

The biggest problem I have with it is that there is absolutely no action, warning or sound when the battery is low. The power-management is setup to hibernate when the battery is low, but no evail. I have also activated the acpi_cpufreq module but no difference.

Acpi set up looks ok to me:

[INDENT][FONT="Lucida Console"]ronald@rasmussen:~$ acpi -V
     Battery 1: charging, 89%, 00:00:28 until charged
     Thermal 1: ok, 44.0 degrees C
     Thermal 2: ok, 44.0 degrees C
  AC Adapter 1: on-line
ronald@rasmussen:~$ more /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      non-rechargeable
design voltage:          125580 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
ronald@rasmussen:~$ more /proc/acpi/battery/BAT0/alarm 
alarm:                   unsupported
ronald@rasmussen:~$ more /proc/acpi/battery/BAT0/
alarm  info   state  
ronald@rasmussen:~$ more /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            782100 mW
remaining capacity:      51630 mWh
present voltage:         unknown
ronald@rasmussen:~$ 
[/FONT][/INDENT]

Does anybody have any hints on how to solve this?

Cheers, Ronald

---

