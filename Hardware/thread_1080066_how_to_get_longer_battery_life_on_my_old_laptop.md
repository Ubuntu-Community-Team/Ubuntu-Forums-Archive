---
title: "how to get longer battery life on my old laptop?"
date: 2009-02-25
forum: Hardware
---

### Post by chanyunkwan on 2009-02-25
HI, guys,

I am using a kind of old laptop, because I still think it works fast enough for me, but it just has a little big too big and heavy. Well, The battery life is pretty awful in actual. It feels like it's less than an hour. But sony says the battery can last for 3hours at most. 
I am wondering if there is any solution for me to make it works longer on battery mode. 
also the power manager on ubuntu8.10(gnome) seems too simple.
Is there a better power manager on gnome? (I don't really like kpowersave)

Link: it's the specification of my VIAO VGN N29vn (If you need more details)
[http://www.vaio-link.com/specifications/specifications.asp?site=voe_en_gb_cons&c=0&s=VGN-N&m=2535&=0&=VGN-N&=2535](http://www.vaio-link.com/specifications/specifications.asp?site=voe_en_gb_cons&c=0&s=VGN-N&m=2535&=0&=VGN-N&=2535)

CPU Intel Core Duo ProcessorT5200
Cache   2048 KB
Memory   2048 MB
Hard Disk Drive   120 Gb (S-ATA) 
Graphic CardIntel Graphics Media Accelerator 950
Video Memory 128 MB
Display 15.4" TFT WXGA 1280x800 (X-black)
Sound Chip Realtek ALC262 High Definition Audio Codec

Thank you so much.

---

### Post by happycube on 2009-02-25
Lithium Ion batteries sadly tend to degrade after a couple of years.   Getting a new battery might be the best fix. :(

Can you copy in /proc/acpi/battery/BAT0/info?  That should say how much capacity the battery still has.  (my actually-somewhat-old Thinkpad T42's extended battery is down from 71.2WH to 43.5WH.  Not terrible considering the battery's three and a half years old, I guess...)

The T5200 is a Core *2* Duo, and with 2GB the laptop should be powerful enough to run ubuntu well for the rest of it's working lifetime.

As for battery life extending tricks... make sure the CPU is being run at mininum speed (copy in /proc/cpuinfo when nothing's running) and run the screen at mininum acceptable brightness.

For other tips, look at 'powertop' which can give you an idea of what's taking up power.

---

### Post by chanyunkwan on 2009-02-25
> **happycube said:**
> Lithium Ion batteries sadly tend to degrade after a couple of years.   Getting a new battery might be the best fix. :(

Can you copy in /proc/acpi/battery/BAT0/info?  That should say how much capacity the battery still has.  (my actually-somewhat-old Thinkpad T42's extended battery is down from 71.2WH to 43.5WH.  Not terrible considering the battery's three and a half years old, I guess...)

The T5200 is a Core *2* Duo, and with 2GB the laptop should be powerful enough to run ubuntu well for the rest of it's working lifetime.

As for battery life extending tricks... make sure the CPU is being run at mininum speed (copy in /proc/cpuinfo when nothing's running) and run the screen at mininum acceptable brightness.

For other tips, look at 'powertop' which can give you an idea of what's taking up power.

Here's what I got from the info file.

present:                 yes
design capacity:         48840 mWh
last full capacity:      48840 mWh
battery technology:      non-rechargeable
design voltage:          124370 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.

---

### Post by happycube on 2009-02-25
Interesting that it still claims 100% life.  I'm a tad sceptical.

Also there are a ton of battery recalls for Sony Li-ion batteries in that timeframe.  You might want to see if there's a recall on your model's battery, in which case you would get a new, longer-lived, and safer battery for free.

Another thing to try is to run it completely down (boot it into the BIOS and don't plug it in until it turns off) and charge it up again.  Sometimes that helps.

---

