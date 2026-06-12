---
title: "Battery Design Charge Meaningless?"
date: 2009-08-24
forum: Hardware
---

### Post by gaussian on 2009-08-24
I have an Asus EEE 1000, and I just bought a new battery from Brilliantstore.com (link: [http://www.brilliantstore.com/asus_laptop_batteries_dekcell_bl_6216h_white.html](http://www.brilliantstore.com/asus_laptop_batteries_dekcell_bl_6216h_white.html)). It seems to be working well, except that gnome-power-manager warns about the battery only having 15% capacity ("old or broken"). I've already disabled the warning. 

Having studied the issue, it looks like this is due to meaningless battery capacity reading (keep in mind, this is Lithium-Ion battery for a netbook), here are the numbers currently given by gnome-power-manager (/proc/acpi/battery/info is same):
```

Product: 1000
Status: Discharging
Percentage charge: 92.0%
Vendor: ASUS
Technology: Lithium ion
Serial number: 
Model: 1000
Charge time: 8 hours 40 minutes
Discharge time: 7 hours 16 minutes
Capacity: 15% (Poor)
Current charge: 75.0 Wh
Last full charge: 81.3 Wh
Design charge: 521.9 Wh
Charge rate: 10.3 W

```

It would seem to me that the designn charge reading is completely meaningless/out of whack (521.9 Wh) and that everything else looks sensible? Anyone understanding anything about batteries (which I don't) care to confirm that. I need to make a decision if I should return the thing or not, but given that it seems to be working I'd like to keep it.

---

### Post by benmoran on 2009-08-24
I'd keep it as long as it's working. I think the design capacity is something that is not reported correctly, because windows doesn't use that info. My OEM Dell inspiron battery is 29wh (crappy battery), but gets reported as 56wh. Now, there IS a 56wh battery from dell also. I suspect they are just reusing the protection boards in the different size packs, regardless of true capacity.

---

### Post by gaussian on 2009-08-24
Great, thank you. I'll just ignore the design charge then.

---

