---
title: "lm-sensors/w83627ehf: Constant input voltage readings"
date: 2014-12-09
forum: Hardware
---

### Post by paulr2 on 2014-12-09
Hi:

I have a Nexcom vehicular console running Ubuntu 14.04 LTS (x86_64) with voltage control enabled in BIOS. I´m using 3.13.0-32 and 3.13.11.10 x86_64 kernels.

I need to check when input voltage is low in order to shutdown the system in proper way before all is halted by BIOS.But no matter if I use lm-sensors from the distribution, or from last source, i always see same input voltages in all sensors (Vcc, CPU,..etc) . I mean, there is no CHANGE in it when I vary input voltage from a variable power supply (with constant current limit to emulate a battery). Curiosly, temperature sensors seem to work with this driver.(and with coretemp) 

By printk-ing this driver source code, recompiling an reloading module (modprobe -force_id 0x8850), i truly see that there is no change in readings. So lm-sensors is not the problem. Does anybody know if this driver w83627ehf.c has support for reading input voltages?. It seems so, but I´m not sure input voltages are really refreshed by kernel after first reading.

Thank you!

---

### Post by Ferhad_Fidan on 2014-12-11
I'm not good at these things but I think you get same readings because voltage regulators on the motherboard outputs a specific voltage no matter how much their input voltage is. The CPU etc. gets these adjusted voltages, so it's not influenced by decreased voltage. No mather the input voltage sensors read the output from voltage regulators and the results are same. But BIOS seems to read a sensor ahead of voltage regulators, and it is maybe BIOS accessible only.

---

### Post by paulr2 on 2014-12-12
Thanks Ferhad.

Yes , that has sense...althought i think that regulators will not be as good to mantain exactly the same voltage when I put power supply a couple of volts down.
Anyway...then, I can´t see the use of those Vcc, Vcpu , 3VCC ..etc voltage measurements lm-sensors has. What would be the reason of having a BIOS voltage detection capable board if I can´t use it in my O.S ?. Well, I´ve asked Nexcom and lets see.

---

### Post by Ferhad_Fidan on 2014-12-15
They are there just to see if there is a problem with voltage regulators. I think they are good enough to maintain the same voltage despite lower input. For example, on notebooks I haven't checked voltages but   14v battery can maintain it for hours and I'm sure the voltages are down at least 1, 2 or 3 volts.Workaround!Maybe the OS can use it but lm-sensors can't! Try running the command: cat /sys/class/power_supply/BAT0/energy_now This gives me the current status of my notebook battery. It starts to decrease from the value /sys/class/power_supply/BAT0/energy_full  shows when notebook is used offline. Also cat /sys/class/power_supply/BAT0/voltage_now gives the voltage and min_voltage_desing gives the desing minimum voltage of battery.So if these commands work, you can do what you want. :) Also try installing powertop and tlp as these will give better battery stats. Install tlp and run sudo tlp stat, this should give some battery status data and paths to read this data. For example my output contains:+++ Battery Status/sys/class/power_supply/BAT0/manufacturer                   = Lenovo IdeaPad/sys/class/power_supply/BAT0/model_name                     = AILZx/sys/class/power_supply/BAT0/cycle_count                    = (not supported)/sys/class/power_supply/BAT0/energy_full_design             =  45820 [mWh]/sys/class/power_supply/BAT0/energy_full                    =  44520 [mWh]/sys/class/power_supply/BAT0/energy_now                     =  44520 [mWh]/sys/class/power_supply/BAT0/power_now                      =      0 [mW]/sys/class/power_supply/BAT0/status                         = Discharging

---

