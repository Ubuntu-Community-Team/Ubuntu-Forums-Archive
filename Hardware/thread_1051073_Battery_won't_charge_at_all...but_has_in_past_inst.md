---
title: "Battery won't charge at all...but has in past installations."
date: 2009-01-26
forum: Hardware
---

### Post by ThunderWhale on 2009-01-26
My battery won't charge when plugged into my AC adaptor, but the percentage doesn't go down either, so it's not a AC adaptor problem.  It does discharge if not plugged in.

On past Ubuntu installations, it has worked just fine.  I have a Dell D410 with stock battery (DEll UY4416) if that helps.

Thank you for any help!

---

### Post by ThunderWhale on 2009-01-28
I've been checking the web, but haven't found anything useful yet...

---

### Post by ThunderWhale on 2009-02-06
Still confused here...

---

### Post by ThunderWhale on 2009-03-25
> **ThunderWhale said:**
> Still confused here...

.

---

### Post by tom56 on 2009-03-25
I think the issue here is that your post isn't very descriptive. What do you mean by it doesn't charge? Do you mean that the icon doesn't show up, or that the battery itself isn't holding a charge at all. If it's the latter it's probably a hardware problem - maybe the battery is just old? After a certain amount of time rechargeable batteries stop holding power.

---

### Post by ThunderWhale on 2009-03-26
I guess it very well could be the battery, but my thought was it was just charging just fine in Windows before I installed Ubuntu (a couple days before writing the first post in this topic.

The battery icon appears in my tray and says it is on AC power, but it says "laptop battery 373 hours and 30 minutes until charged, and the icon is always down in the "red" bar.   When I try to run without the power cord, it just discharges and is currently at 24%...it never goes up.    It just doesn't seem like a hardware problem, because it worked fine in Windows a couple weeks ago.

---

### Post by krucifux on 2009-08-10
I had the same problem with my d410. It would work just fine when plugged in but the battery would not charge. It turned out to be the pin inside the power adapter tip had broken off. Once I had replaced the adapter everything was fine.

---

### Post by cdoss on 2009-08-22
I am also having this problem in 9.04.  The battery is new (as in, I installed it within the last week and just discharged it down to 6% for the first time).  

Output of acpi -V :
     Battery 0: Full, 6%
     Battery 0: design capacity 43950 mAh, last full capacity 43950 mAh = 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 47.0 degrees C
     Thermal 1: ok, 51.0 degrees C
     Cooling 0: LCD 0 of 15
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10

Note it says "Full, 6%".  

I have seen the link here [https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery)  but i'm not sure it's still relevant, since the DSDT link is deprecated now (has nothing for my lenovo t61).

Something else that is odd: as per some instructions on the above link, i tried
> sudo rmmod acpi_sbs
ERROR: Module acpi_sbs does not exist in /proc/modules
> sudo rmmod battery
ERROR: Module battery does not exist in /proc/modules
> sudo modprobe battery
FATAL: Module battery not found.

I don't know what any of this means or if the two are probably related.  

Let me know what more information i should give.  The computer is a 1.5 year old lenovo t61.  
Help please?

---

### Post by cdoss on 2009-08-22
Also, if i unplug the charger and run acpi -V i get
     Battery 0: Discharging, 6%, 00:09:31 remaining
     Battery 0: design capacity 43950 mAh, last full capacity 43950 mAh = 100%
  AC Adapter 0: off-line
     Thermal 0: ok, 39.0 degrees C
     Thermal 1: ok, 44.0 degrees C
     Cooling 0: LCD 7 of 15
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10

---

### Post by cdoss on 2009-08-22
Also, I didn't buy the new battery from lenovo, i got it from an online vendor.  It worked fine when i let it discharge a little bit and charge a little bit for the past week.  I have no idea if there are differences between batteries sold from lenovo and from other vendors or what they might be.

---

### Post by cdoss on 2009-08-23
Also, I realized I hadn't gotten rid of my old battery, so i tried it.  It has very low capacity, but still charges and discharges.  So, perhaps it is the battery i got from ebuybatteries.com.  Not sure that's the issue, but maybe i'll have to buy the battery from lenovo ...

---

