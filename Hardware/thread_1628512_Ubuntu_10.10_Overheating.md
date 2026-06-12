---
title: "Ubuntu 10.10 Overheating"
date: 2010-11-22
forum: Hardware
---

### Post by johnproyal on 2010-11-22
Today the fan has been very volatile. It seems to be turning off and on at whim, not starting on some boots and starting on others. Like this one. (Though I haven't heard it for a few minutes, to be honest.) I'm paranoid it'll shut off in a few minutes, which its been doing all day.

I'm on a Toshiba L505D-S5983 laptop. I installed the ACPI package, and ran acpi -V in the terminal, this is what it displayed:

```
Battery 0: Discharging, 90%, 01:21:22 remaining
Battery 0: design capacity 4000 mAh, last full capacity 3260 mAh = 81%
Adapter 0: off-line
Thermal 0: ok, 81.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 105.0 degrees C
Cooling 0: LCD 4 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 10
Cooling 3: Fan 0 of 1

```

I'm not sure if its a problem with the ACPI or the hardware. The fan also didn't start in the Windows partition on this laptop, which had me pretty worried, but when I started it up this time the fan started like normal (well, started) and I haven't heard it since.

If there's any other information needed, let me know. I need to get this fan problem solved: I shouldn't have to hope its going to work, it should work.

Thanks for any help.

---

### Post by Fafler on 2010-11-23
You could use a utility like fancontrol to override the BIOS. I don't k now if it will work on your machine, though. Theres also a package names toshutils that might be interesting, but the description tells its mostly for older laptops.

---

