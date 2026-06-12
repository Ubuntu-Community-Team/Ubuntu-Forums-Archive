---
title: "HP dv6000 battery issues"
date: 2011-12-28
forum: Hardware
---

### Post by yoramdavid on 2011-12-28
I have a HP dv6000 laptop, Ubuntu 11.10 gnome-cassic environment.

I recently bought a new battery for my laptop to replace the 5-years old dead one.
10 days ago to be exact.

The battery was working (charging and powering the computer when no power plugged in) until yesterday.
Now it does not charge, it says it has 12,9% charge and that it is charging.
Status goes from "fully charged" to "charging" but is has no energy at all and does not charge.

Can someone please help me with this?
Thank you.

Battery specs:
[HTML]DC 10.8V 4800mAh/52Wh
Replace: HSTNN-DB31[/HTML]

This is the information I got from the command "cat info":

```
cat info
present:                 yes
design capacity:         6000 mAh
last full capacity:      2976 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 152 mAh
design capacity low:     92 mAh
cycle count:		  0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```

Here is the information I got from gnome-power-statistics:
(note that the capacity indicates 49.6%)

[HTML]Device			battery_BAT0
Type			Laptop battery
Vendor			Hwelett-Packard
Model			Primary
Supply			Yes
Rereshed		0 seconds
Present			Yes
Rechargeable		Yes
State			Charged ^ Charging (battery icon comes and goes from taks bar
Energy			5.7 Wh
Energy when empty	0.0 Wh
Energy when full	44.0 Wh
Energy (design)		88.8 Wh
Rate			0.0 Wh
Voltage			10.9 V
Time to full		0 seconds
Time to empty		0 seconds
Percentage		12.9% (if ac unplulgged, computers goes down)
Capacity		49.6%
Technology		Lithium Ion[/HTML]

Are there any other tests I can do?

I do not know if this is important, but here are the specifications of the battery I had before:

[HTML]DC 10.8V 47Wh
HSTNN-DB42
For use with HP Series HSTNN-W20C, HSTNN-W34C, HSTNN-Q21, family of cumputer products only
Label with: "Replace with HP Spare 441425 - 001
7F034"

Label with: "CT:6301601BBU8FZ1"[/HTML]

From gnome-power-statistics:

[HTML]Device			battery_BAT0
Type			Laptop battery
Vendor			Hwelett-Packard
Model			Primary
Supply			Yes
Rereshed		0 seconds
Present			Yes
Rechargeable		Yes
State			Charged ^ Charging (battery icon comes and goes from taks bar
Energy			0.0 Wh
Energy when empty	0.0 Wh
Energy when full	88.8 Wh
Energy (design)		88.8 Wh
Rate			0.0 Wh
Voltage			7.2 V
Time to full		0 seconds
Time to empty		0 seconds
Percentage		0.0% (if ac unplulgged, computers goes down)
Capacity		100.0%
Technology		Lithium Ion[/HTML]

I removed the new battery and placed the old one, ran the "cat info" command and got the exact same results as for the new one:

```
cat info
present:                 yes
design capacity:         6000 mAh
last full capacity:      2976 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 152 mAh
design capacity low:     92 mAh
cycle count:		  0
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```

---

### Post by searchfgold6789 on 2011-12-28
You should probably replace the battery.

---

### Post by Scott Baker on 2011-12-29
This is going to sound quite obvious, but did you get your battery from a trusted source? Sorry to say this, but some internet based resellers are less than reputable. You said this battery worked for about a week before this issue. The info you provided doesn't appear unusual other than the fact that you battery is* refusing* to charge. What you may have received would be known as "new old stock". This is a product that while never having been used, and still in its original packaging, may have been sitting on a shelf for* YEARS*. If this is the case, you'll continue to have problems with this battery. Try a replacement if the vendor will comply, and see if that corrects the issue.

---

### Post by Moozillaaa on 2011-12-29
See my post [here](http://ubuntuforums.org/showpost.php?p=11571823&postcount=5).

---

### Post by yoramdavid on 2011-12-29
> **Scott Baker said:**
> This is going to sound quite obvious, but did you get your battery from a trusted source? Sorry to say this, but some internet based resellers are less than reputable. You said this battery worked for about a week before this issue. The info you provided doesn't appear unusual other than the fact that you battery is* refusing* to charge. What you may have received would be known as "new old stock". This is a product that while never having been used, and still in its original packaging, may have been sitting on a shelf for* YEARS*. If this is the case, you'll continue to have problems with this battery. Try a replacement if the vendor will comply, and see if that corrects the issue.

Thank you Scott Baker,

I had it bought for me in a shop in Jakarta (Indonesia), which is where I am now. It has guarantee, so I will send it back for testing/replacement. Till then, I'll have to live without battery I guess.
I am not sure about the source being good or bad.

Regards,

Yoram

---

### Post by yoramdavid on 2011-12-29
> **Moozillaaa said:**
> See my post [here](http://ubuntuforums.org/showpost.php?p=11571823&postcount=5).

Thank you Mozillaaa,

I will give your post a try:

> Some batteries' BIOS monitoring needs occasional re-calibration.

Bring up BIOS/setup menu, battery power, and let it run OUT with no safety shutdown.

Then plug it in, and allow it to charge with EVERYTHING running. The longer it takes to fully re-charge, the better. Boot Windows, put in a DVD, plug in some USB devices, etc.

---

### Post by bailunrui on 2012-08-22
I'm having this exact issue. What worked for you, yoramdavid?

---

### Post by yoramdavid on 2012-08-22
> **bailunrui said:**
> I'm having this exact issue. What worked for you, yoramdavid?

Hi bailunrui,

I had the battery replaced and this one is now good.
So, no tricks were used which could help you, sorry.

Yoram

---

