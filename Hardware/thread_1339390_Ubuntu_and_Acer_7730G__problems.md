---
title: "Ubuntu and Acer 7730G  problems"
date: 2009-11-27
forum: Hardware
---

### Post by filip007 on 2009-11-27
Laptop battery not detected properly 
Missing menu icons (fixed with Show menu icons)
1152x864 boot resolution error (todays laptops use wide resolutions OK)

I install ACPI with...sudo apt-get install acpi

This is on AC:
acpi --everything
Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 4234 mAh = 96%
Adapter 0: on-line
Thermal 0: ok, 50.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Cooling 0: LCD 0 of 9
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

This is on battery:
acpi --everything
Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 4234 mAh = 96%
Adapter 0: off-line
Thermal 0: ok, 52.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Cooling 0: LCD 0 of 9
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

It's working sort of and i have add battery icon to panel.

Suspend is working.
Brightness is not reduced when on battery!
Battery tab is missing on Power Management window! :-#

OK i have done Power config that works for both ways for AC and battery and have added more delay on backlight dim for 2min after 5min black screensaver kicks in and after 30min the all system goes to sleep and i like it this way. 

I like to enjoy my laptop not testing it...so less custom config the better :roll:

---

