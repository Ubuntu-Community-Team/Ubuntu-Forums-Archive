---
title: "laptop battery capacity differs in ACPI and on sticker."
date: 2010-02-08
forum: Hardware
---

### Post by PanCiasteczko on 2010-02-08
Hi,
I bought a new battery for a netbook. 
The sticker that looks original with all certifications and stuff says it is a 9 cell battery with **7800 mAh** capacity. But:
```
cat /proc/acpi/battery/BAT1/info
```
says:
```

present:                  yes
design capacity:          6600 mAh
last full capacity:       6550 mAh
battery technology:       rechargeable
design voltage:           11100 mV
design capacity warning:  0 mAh 
design capacity low:      0 mAh 
capacity granularity 1:   1 mAh
capacity granularity 2:   1 mAh
model number:             MS-N011

serial number:

battery type:             LION

OEM info:                 MSI Corp.

```
Can ACPI be wrong on this? Or was I simply cheated?

---

### Post by tgalati4 on 2010-02-08
Fake battery is a possibility.  Exercise it a few times and see if the the "last full capacity" exceeds the design specification.  Sometimes batteries are rated lower for warranty purposes (80% capacity for 2 years or 300 cycles whichever occurs first).

Since this is a netbook, the focus is on low-cost.  So I wouldn't be surprised if your batteries contain catfood.

Catfood is cheaper than lithium and probably less poisonous.

---

### Post by PanCiasteczko on 2010-02-08
I have tested it few times already and id does not exceeds 6600

> **tgalati4 said:**
>  Sometimes batteries are rated lower for warranty purposes 

Yea, but if it was rated lower it should also say 6600 mAh on the sticker and should be sold as 6600 mAh, am I right?

---

### Post by tgalati4 on 2010-02-09
Where is the battery made?

---

### Post by Megatog615 on 2011-02-13
Bump.

I found this thread on Google, and I was wondering how PanCiasteczko resolved this(if at all).

I have purchased a 7800mAh battery off ebay, like PanCiasteczko, for my Acer Aspire One D150. It reports the same 6600mAh design capacity. I have done some full discharges(charging to 100%, then rebooting and loading the BIOS setup and letting it discharge all the way until it turns off) and now, the 'Last full capacity' has exceeded 6600(currently, 7221 mAh), but the design capacity still remains at 6600.

I'm starting to think that this is a legitimate 7800mAh battery, but the design capacity is programmed wrong(or Linux ACPI has a few bugs).

Any additional thoughts on this would be appreciated.

---

