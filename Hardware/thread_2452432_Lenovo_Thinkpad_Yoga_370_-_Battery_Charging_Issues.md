---
title: "Lenovo Thinkpad Yoga 370 - Battery Charging Issues"
date: 2020-10-21
forum: Hardware
---

### Post by kg6gfq2 on 2020-10-21
My Thinkpad 370 won't charge its battery!  This is a used laptop, recently purchased off ebay.  I tried a new battery to no avail.  It works fine plugged in to AC, but immediately upon unplugging the computer turns off.  tlp-stat and the Power Settings dialog both claim it's charging, but acpi says it is "charging at zero rate".  

I realize this may be a hardware issue, but some online research indicates it might be a firmware problem that can be fixed from the OS, and I'd like to explore that before I go poking around with a multimeter or give up and return the laptop.  One of the common recommendations for charging problems on Lenovo laptops is to update the BIOS, but the BIOS update utility - both the one in Windows and the one on a bootable drive - require that the battery be fully charged.  

Some info that may be useful:

```
$ sudo tlp-stat -b
--- TLP 1.3.1 --------------------------------------------

+++ Battery Features: Charge Thresholds and Recalibrate
natacpi    = active (data, thresholds)
tpacpi-bat = inactive (kernel module 'acpi_call' not installed)
tp-smapi   = inactive (ThinkPad not supported)

+++ ThinkPad Battery Status: BAT0
/sys/class/power_supply/BAT0/manufacturer                   = SMP
/sys/class/power_supply/BAT0/model_name                     = 00HW027
/sys/class/power_supply/BAT0/cycle_count                    =      1
/sys/class/power_supply/BAT0/energy_full_design             =  44000 [mWh]
/sys/class/power_supply/BAT0/energy_full                    =  43190 [mWh]
/sys/class/power_supply/BAT0/energy_now                     =      0 [mWh]
/sys/class/power_supply/BAT0/power_now                      =      0 [mW]
/sys/class/power_supply/BAT0/status                         = Charging

/sys/class/power_supply/BAT0/charge_start_threshold         =     96 [%]
/sys/class/power_supply/BAT0/charge_stop_threshold          =    100 [%]

Charge                                                      =    0.0 [%]
Capacity                                                    =   98.2 [%]

+++ Recommendations
* Install acpi_call kernel module for ThinkPad battery recalibration


```

```
$ acpi -V
Battery 0: Charging, 0%, charging at zero rate - will never fully charge.
Battery 0: design capacity 3182 mAh, last full capacity 3123 mAh = 98%
Adapter 0: on-line
Thermal 0: ok, 42.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: intel_powerclamp no state information available
Cooling 2: Processor 0 of 10
Cooling 3: pch_skylake no state information available
Cooling 4: Processor 0 of 10
Cooling 5: x86_pkg_temp no state information available
Cooling 6: iwlwifi 0 of 19
Cooling 7: Processor 0 of 10
Cooling 8: iwlwifi_1 no state information available


```

Cross-posting to the Lenovo Community Forums in case they have ideas: [https://forums.lenovo.com/t5/ThinkPad-S-Series-ThinkPad-Yoga-and-Twist-Laptops/Lenovo-Thinkpad-Yoga-370-Battery-Charging-Issues/m-p/5045375?page=1#5166555](https://forums.lenovo.com/t5/ThinkPad-S-Series-ThinkPad-Yoga-and-Twist-Laptops/Lenovo-Thinkpad-Yoga-370-Battery-Charging-Issues/m-p/5045375?page=1#5166555)

Any idea what might be causing this, or how to go about fixing it?  Anything else I should check, other information that might help with diagnosis?

Thank you!

Darin

---

### Post by Autodave on 2020-10-22
What happens if you leave the laptop powered off and the AC adapter plugged in for 8 hours or so?  Does the battery charge then?

---

### Post by kg6gfq2 on 2020-10-22
> **Autodave said:**
> What happens if you leave the laptop powered off and the AC adapter plugged in for 8 hours or so?  Does the battery charge then?

Nope!  Tried that; no such luck.  Also tried "unplug it and take out the battery and hold down the power button to reset everything" to no avail.  

Thanks, though!

---

### Post by CelticWarrior on 2020-10-22
Have you tried the actual reset method for your model?
[https://forums.tomsguide.com/faq/how-to-fix-charging-problems-in-lenovo-yoga-laptops.188342/](https://forums.tomsguide.com/faq/how-to-fix-charging-problems-in-lenovo-yoga-laptops.188342/) -> Chapter 10

Taking out the battery and holding down the power button resets absolutely nothing. It is done occasionally to dissipate static electricity that can cause some issues. I've heard of some Dell desktops not booting because of that. Unplugging the power cord and pressing the power button for a few seconds would make them boot again. Unheard of for laptops.

---

### Post by kg6gfq2 on 2020-10-22
> **CelticWarrior said:**
> Have you tried the actual reset method for your model?
[https://forums.tomsguide.com/faq/how-to-fix-charging-problems-in-lenovo-yoga-laptops.188342/](https://forums.tomsguide.com/faq/how-to-fix-charging-problems-in-lenovo-yoga-laptops.188342/) -> Chapter 10

Taking out the battery and holding down the power button resets absolutely nothing. It is done occasionally to dissipate static electricity that can cause some issues. I've heard of some Dell desktops not booting because of that. Unplugging the power cord and pressing the power button for a few seconds would make them boot again. Unheard of for laptops.

Ok, tried that too.  Still nothing.

---

