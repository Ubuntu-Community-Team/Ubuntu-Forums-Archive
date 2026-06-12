---
title: "Laptop battery info"
date: 2011-02-11
forum: Hardware
---

### Post by minche on 2011-02-11
I get this


```
cat /proc/acpi/battery/C241/info
present:                 yes
design capacity:         182 mAh
last full capacity:      182 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 10 mAh
design capacity low:     2 mAh
capacity granularity 1:  100 mAh
capacity granularity 2:  100 mAh
model number:            Primary
serial number:           00522 2009/05/09
battery type:            LIon
OEM info:                Hewlett-Packard

```

first, it showed that battery is 48% charged and it wasn't charging it, and info read design capacity as 370mAh
when I restarted it I got this info :S

laptop is Compaq 610 with Ubuntu 10.04

---

### Post by minche on 2011-02-11
yeah, but 182 mAh can't be right (for design capacity)
and it dropped just after it 'refused' to charge :S

---

### Post by minche on 2011-02-12
now I got this
```
Battery 0: Full, 100%
Battery 0: design capacity 407 mAh, last full capacity 407 mAh = 100%
Adapter 0: on-line

```

and yesterday it was 670 :S
that just can't be normal

---

### Post by georgemc on 2011-02-12
OK I do not have the same laptop, I have a olde A2500H running U10.04.1LTS, however, I feel that your design capacity is on the low side and it shouldn't be bouncing around like that.
 

 In my Laptop's BIOS I can recalibrate the battery, which I did just recently because the displayed last full capacity number was really low, which can indicate a battery going dead.
 

 I timed the recalibration of  the battery to verify that the full capacity was in a sane range.  I.E it did take 2 hours to completely discharge which does correspond to the max capacity on that make/model.
 

 I would suggest to look into the BIOS and see if you can recalibrate the battery.
 

 Hope this helps.
 

 George

---

### Post by minche on 2011-02-13
and now this 
```
acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 1 mAh, last full capacity 0 mAh = 1%

```

@georgemc thanks for that, I will see if I have that option :D

---

