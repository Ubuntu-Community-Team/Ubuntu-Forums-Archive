---
title: "I`ve written a Powersave Skript,help me 2 get it Working"
date: 2009-03-19
forum: Hardware
---

### Post by starfly on 2009-03-19
Hello,

My Notebook, uses 20Watts in Normal Mode, so ive startet Powertop and confirmed every command, he suggests to save power...And wow, ive got 12 Watts after it !

So my idea was, copy the Commands out of Powetop, put them into a textdata sheet, and make it runable...

But the problem is, theres no effect.when i start powertop after runnig my skript, thres still 20 watts, and only after cofirming the commands again ( same as in the script) the watts were less.

So heres the script, tell me what to do that it will do the same like powertop :-) Maybe heres a professor around, who could give me a hint , how to implement it, when i plug out the ac adaptor, that it will run automaticaly.

Greetz



#Wlan Powersave

echo 5 > /sys/bus/pci/drivers/iwl3945/0000:08:00.0/power_level

#Dirty Writeback

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

#Govenor Cpu Speed

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

#HDD Drivedown

echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

#Dvd Polling aus

hal-disable-polling --device /dev/cdrom

---

