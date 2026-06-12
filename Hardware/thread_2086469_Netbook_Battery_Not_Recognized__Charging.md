---
title: "Netbook Battery Not Recognized / Charging?"
date: 2012-11-21
forum: Hardware
---

### Post by Dorzu on 2012-11-21
I have an old Asus 1000HE that has been running current versions of Ubuntu since it was released (on current 12.04 now). I've never had any problems until a storm last week. The netbook wouldn't turn on, clearly a power issue. I bought a new charger and battery. With the new charger / battery, it turns on but immediately hibernates if AC power is removed. 

Symptoms: The orange battery light is flashing. (ASUS manual says this means it is charging.) The power manager in the task bar reads "(not present)". The netbook hibernates without an AC cord connected, as if it is receiving no power from the battery.

I've seen some requests for the below info in other threads, so I'll include it here. I didn't include acpi_listen but it does respond to (dis)connecting the AC cord. 

cat /proc/acpi/battery/BAT0/info
```
present:                 yes
design capacity:         9734 mAh
last full capacity:      9324 mAh
battery technology:      rechargeable
design voltage:          8400 mV
design capacity warning: 933 mAh
design capacity low:     467 mAh
cycle count:		  0
capacity granularity 1:  97 mAh
capacity granularity 2:  97 mAh
model number:            1000HE
serial number:            
battery type:            LION
OEM info:                ASUS
```

cat /proc/acpi/battery/BAT0/state
```
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            124 mA
remaining capacity:      0 mAh
present voltage:         8248 mV
```

dmesg | grep battery
```
[    0.436272] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.436302] ACPI: Battery Slot [BAT0] (battery present)
[    0.606616] ACPI: Battery Slot [BAT0] (battery present)
```

acpi -V
```
Battery 0: Charging, 0%, 75:11:36 until charged
Battery 0: design capacity 9734 mAh, last full capacity 9324 mAh = 95%
Adapter 0: on-line
Thermal 0: ok, 49.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 85.0 degrees C
Thermal 0: trip point 0 switches to mode passive at temperature 82.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
```

I read [this thread]("http://askubuntu.com/questions/9401/on-battery-is-not-recognized") but the netbook will not power on without the battery in the slot. I also saw a complicated DSDT+iasl solution for Toshibas but I'm not sure if that would help me, or is even my problem. 

Thanks for even taking the time to read this mammoth post. I tried to include as much as I could upfront. Any suggestions are welcome and appreciated.

---

### Post by ahallubuntu on 2012-11-21
> **Dorzu said:**
> I have an old Asus 1000HE that has been running current versions of Ubuntu since it was released (on current 12.04 now). I've never had any problems until a storm last week. The netbook wouldn't turn on, clearly a power issue.

Does this mean the netbook took a power surge?  It obviously could have blown out the charger and also caused other damage - not just to the battery but to the motherboard.

> I bought a new charger and battery. With the new charger / battery, it turns on but immediately hibernates if AC power is removed. 

Are they exact replacement parts or are they "generic?"

> Symptoms: The orange battery light is flashing. (ASUS manual says this means it is charging.) The power manager in the task bar reads "(not present)".

Did the orange battery light flash previously when things were working fine, when the battery was charging?  I am not familiar with this model, but generally a flashing light doesn't mean "charging," it indicates a problem.  That would be consistent with a battery that is almost dead and not charging at all - only has a small charge left on it from when you got it but enough, apparently, to hibernate the laptop (are you sure it's really hibernating?  Does it resume successfully afterward if you plug the power back in.

> The netbook hibernates without an AC cord connected, as if it is receiving no power from the battery.

Hibernation requires power to save the state of the memory to a file on the hard drive - see above.  Maybe it's not really hibernating and just losing power immediately?  (Completely dead battery?)

My guesses:

1. Power surge damaged power circuits on the motherboard (probably not worth fixing).
2. Charger isn't quite compatible with the laptop - will power the laptop but not charge the battery.  This could happen if charger can't supply enough current but a netbook shouldn't require much current so unlikely.  More common of Dell models to sense the charger type and not charge a battery if not sensed correctly.
3. Battery is not compatible with the netbook or is just bad.

Do you have the original battery?  What does it do if you plug it in now?  Same thing?

---

### Post by Dorzu on 2012-11-21
> **ahallubuntu said:**
> Does this mean the netbook took a power surge?  It obviously could have blown out the charger and also caused other damage - not just to the battery but to the motherboard.

I was asleep but I expect there was a power surge, yes. You're right that the motherboard is a possibility, but I was hoping not.

The charger is a universal from Best Buy. The battery comes from ASUS itself as a possible replacement for multiple models. I'd expect that to mean the battery works, but it's not for this model alone.

> 
Did the orange battery light flash previously when things were working fine, when the battery was charging? 
The orange light did flash, slowly, as it is now.

> Maybe it's not really hibernating and just losing power immediately?  (Completely dead battery?)
This seems to be the case. It does not appear to be properly hibernating (it does not resume) but it does make the attempt before dying.


> 
2. Charger isn't quite compatible with the laptop - will power the laptop but not charge the battery.  This could happen *if charger can't supply enough current* but a netbook shouldn't require much current so unlikely. 
3. Battery is not compatible with the netbook or is just bad.

Do you have the original battery?  What does it do if you plug it in now?  Same thing?

This...is interesting. Previously, when it did not boot, I let it charge for a full day before deciding that one of the parts must be bad. I have now tried all combinations of the parts and found this: 
[LIST=1]
[*]The new battery does not work, regardless of charger. The system boots but shows the above issues. I assume point #3 is correct:  This replacement is incompatible or -something- in Ubuntu needs to be changed to accommodate it.
[*]However!, point two also looks correct. The old battery...now... works? I have no idea why. This is baffling. With the old charger (which is also working?), the reported time until charged (via acpi) is half of the time with the new charger. The replacement charger is not supplying enough current to compete with the model-specific charger.
[/LIST]

It looks like you were correct. I'm not sure why the old parts are working again, but the new ones are obviously not doing the job. After letting the old battery charge to 25%, I tried it off battery with no issues. It's now charging to full. I guess this is resolved. Thanks.

---

