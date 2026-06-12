---
title: "Battery is Charged, Yet Without the Charger Laptop Won't Work"
date: 2010-09-11
forum: Hardware
---

### Post by abeherbert91 on 2010-09-11
So, this just started for the first time, and I have never had this problem before...

I have an Acer 5810TZ and this morning after I restarted my laptop and took my laptop off of the charger, it turned off... I tried to turn it back on, and well, it didn't work. My computer would not cut on at all until I plugged in my laptop charger.

If anybody could have any idea as to what's going on, please let me know...

:confused:

Oh, and just a heads up: I check the battery status and my battery is fine. Also, it's fully charged. I have no idea what's going on...

---

### Post by gzarkadas on 2010-09-11
Either the battery is old and it can't give power anymore (they degrade with use and although appear fully charged in your panel they cannot last long; they discharge rapidly - depending on how you use them this may happen after a couple of years even for the high-brand models) or it developed a fault (maybe a short circuit inside one of its cells or something else). It may also be the case that something (usually dirt) has covered one or more of its pins and stopped the electrical contact.

So, first check its contacts and whether it is positioned right in its place. Then, if it is more than 2 years old. Check also if it gets hot while in your laptop; this may be an indication of a short circuit. 

Unless this is a dirty contacts/wrong fitting problem, your battery will need a replacement; don't try to repair it your self - lithium batteries (and not only them) *_can be dangerous_* if not properly handled.

---

### Post by Tony221268 on 2010-10-06
I get the same deal on an NC10 Samsung - battery says it is charged, but unplugging causes the laptop to power off. Googling, I see lots of misreporting batteries that people are calling "dead batteries" but I suspect that at least in some cases the problem is Ubuntu, not the battery. 

Why?

Several reasons: because this laptop just changed from XP to Ubuntu and suddenly the battery broke in sync with the OS. 

Also, if left powered down completely (so left off for several hours), suddenly I can charge it. Almost as if it needs to be "clear" of the OS before it agrees to charge.

Finally, while I am no expert, this stuff from investigating the battery says to me that something is not being reported properly:

present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      0 mAh
present voltage:         11337 mV
present:                 yes
design capacity:         5200 mAh
last full capacity:      0 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            
serial number:           
battery type:            LION
OEM info:                SAMSUNG Electronics

---

### Post by phredbull on 2010-10-06
The same thing happened to my battery. I believe it is because power management wasn't working properly for my machine, and when the battery got low, instead of shutting down, it just let the battery drain completely, which kills li-ion batteries.

---

### Post by gzarkadas on 2010-10-06
As reported in [wikipedia]("http://en.wikipedia.org/wiki/Lithium-ion_battery") li-ion batteries do loose capacity as times passes: 20% per year which can be much more if the battery frequently is under elevated temperatures (from poor ventilation, such as when placing your laptop on your bed, or from use in high-temperature places, etc.). Furthermore, over-discharge may trigger internal safety circuits that do not allow recharging of the battery by normal chargers (such as the ones supplied by the laptop manufacturer). 

When either time or an over-discharge event brings the battery to this state of not sustaining operation for even a minute, the only sensible thing an average user can do is to order a replacement battery.

I do not believe it is an OS-specific fault; I have seen laptop batteries gradually gone "dead" under both windows and linux.

---

### Post by psusi on 2010-10-06
> **Tony221268 said:**
> 
last full capacity:      0 mAh


That says the battery won't hold a charge.  It is shot.

---

### Post by phredbull on 2010-10-07
> **gzarkadas said:**
> I do not believe it is an OS-specific fault; I have seen laptop batteries gradually gone "dead" under both windows and linux.
All of what you said is certainly true, BUT it is also true that power management in Ubuntu has not been functional, at least on my laptop. I would fall asleep with my computer on battery power, and when I woke up, the battery would be dead. No auto-shut down, like I have set in the Power Management preferences. 10.04 is the first time I can successfully wake up from suspend, and even now, it works about 75% of the time.
:?

---

### Post by toddpedlar on 2010-10-09
> **gzarkadas said:**
> Either the battery is old and it can't give power anymore (they degrade with use and although appear fully charged in your panel they cannot last long; they discharge rapidly - depending on how you use them this may happen after a couple of years even for the high-brand models) or it developed a fault (maybe a short circuit inside one of its cells or something else). It may also be the case that something (usually dirt) has covered one or more of its pins and stopped the electrical contact.

So, first check its contacts and whether it is positioned right in its place. Then, if it is more than 2 years old. Check also if it gets hot while in your laptop; this may be an indication of a short circuit. 

Unless this is a dirty contacts/wrong fitting problem, your battery will need a replacement; don't try to repair it your self - lithium batteries (and not only them) *_can be dangerous_* if not properly handled.

I'm having the same kind of problem with my Serval Pro (vintage 2007).  I bought two 9-cell batteries with the computer, and have replaced one recently. The behavior of the old battery and the replacement is essentially identical.  That is, it seems not to charge at all while on AC.  

From the Power Statistics thingy the claim is "fully charged" and simultaneously Energy is "3.0 Wh".  Energy when full should be about 80 Wh, so I don't get that.  The battery is absolutely not doing anything charging-wise - when I mouse-over the battery icon in the top bar, it says "fully charged", consistent with what the Power Statistics program thinks.  

When I check the battery status file, I get:

todd@bohr:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      273 mAh
present voltage:         10826 mV


Any ideas?  I have almost identical results with the 3 year old batter as with the above, which was taken with the 3 month old replacement battery.

Todd

---

### Post by Quackers on 2010-10-09
This happened to me a couple of years ago. The battery is finished. It's nothing to do with the OS (the battery has its own safety features built in which don't allow over-charging or over-use). One day you wake up and it just doesn't work any more.

---

### Post by toddpedlar on 2010-10-09
> **Quackers said:**
> This happened to me a couple of years ago. The battery is finished. It's nothing to do with the OS (the battery has its own safety features built in which don't allow over-charging or over-use). One day you wake up and it just doesn't work any more.

The battery that I just bought (and haven't used much if at all) is toast, then?  I could believe it of the older battery, but the new one?  Makes no sense...

---

### Post by psusi on 2010-10-10
What does the info file say?  That voltage is rather low.  If you unplug and run off the battery for a few minutes, then plug it in, do you see some charge current going in?

---

### Post by Quackers on 2010-10-10
Toddpedlar, if you've had the "new" battery for some time but never used it, it is possibly beyond help. My HP laptop battery (some years ago now) only lasted 8 months. As it was only guaranteed for 6 months HP basically said "tough luck" and I had to buy another. They told me that they need to be used at least once a month until almost completely discharged and then re-charged overnight when the laptop is switched off. As I had used my laptop almost exclusively plugged in to the mains supply my battery died quickly. I am also told that they don't like being left in a fully discharged state for long periods.
With my current laptop I use the battery about once a month and it has lasted 3 years now.

---

### Post by gzarkadas on 2010-10-10
> **toddpedlar said:**
> The battery that I just bought (and haven't used much if at all) is toast, then?  I could believe it of the older battery, but the new one?  Makes no sense...

If you bought them together with your computer (as you mentioned in your first post) and did *_not_* periodically recharged the replacement battery, but let it staying on a shelf, then it can make sense. Most probably the replacement battery got completely discharged and now needs special chargers to revive it (if it is at all possible). See [this link]("http://en.wikipedia.org/wiki/Lithium-ion_battery#Shelf_life") (scroll down to subsection "Safety requirements"). Here is [another reference link]("http://batteryuniversity.com/parttwo-34.htm") that also contains useful information about lithium batteries.

---

### Post by say.hello.to.anna on 2010-11-06
Hi, 

I think my laptop may provide some answers. When I unplug the charger it immediately shuts down (sometimes it seems to go to sleep instead?) BUT I can switch it on, with NO charger, STRAIGHT AWAY and it works as normal without the changer plugged in for several hours (even though its a very old computer that previously had xp 97 on it, and did not have this problem before ubuntu install).

I also have a problem with the wireless/Internet becoming disabled after it goes to sleep. Only way to solve it is to restart it.

I have checked the options in my inexpert way but have found no command to provoke such behavior. 

I'm sorry guys but I think this is a soft, not hard ware issue.

anyone fancy fixing this? Its annoying cause the thing shuts down if i unplug by accident, if I am working in bed etc.

Anna

---

### Post by g123386761 on 2011-03-24
Basically all I did was I took the laptop battery out, started the system, reinstalled power management from the ubuntu software center, rebooted with the battery and all was well!

---

