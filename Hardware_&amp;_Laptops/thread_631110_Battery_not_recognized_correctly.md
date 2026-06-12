---
title: "Battery not recognized correctly"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by schierly on 2007-12-04
I hope this is the right place to post this topic.

I have an Acer Travelmate 800 laptop. It was running on feisty with a 4400mAh battery. I upgraded to gutsy. After this I replaced the old battery with a new one with 5200mAh.
Unfortunately it seems that the new battery is only recognized with the old capacity.
The battery label says 5200mAh, so I actually don't think the battery is faulty.
I cannot exclude that maybe the dealer cheated at me. On the dealer's website this new battery should be compatible with my laptop.

Is it possible that Ubuntu stores the battery information statically?
Where does the System gets the information? (BIOS, ACPI)

I haven't had the chance to check what is Windows XP saying about the capacity, but will try it today.
I will also tray if maybe a BIOS Update helps.

Solutions, Help and Information is very welcome!

---

### Post by schierly on 2007-12-04
OK, I did some checks:

BIOS is on the last available version!

I checked Windows XP, It's recognized as 4400mAh, but not directly. Instead its
reported as about 67120mWh which means 4400mAh at 15,25 V (calculated), which seems logically.

There are only two options:

First one, somebody sold an 4400mhA battery as an 5200mhA,
or second one, the BIOS only reports 4400mAh which is possible but not very likely as I
have an uptodate BIOS Version and the partnumbers should be compatible with the replaced battery.

I actually discharged the battery until it switched off and recharged it. But there is no change.

So has anyone had an experience like me?

---

