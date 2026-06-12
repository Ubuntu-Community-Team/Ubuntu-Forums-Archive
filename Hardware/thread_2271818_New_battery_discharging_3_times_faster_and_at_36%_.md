---
title: "New battery discharging 3 times faster and at 36% of capacity"
date: 2015-04-01
forum: Hardware
---

### Post by banchshee on 2015-04-01
Hello,

just wrote a whole post, but everything freezed, so I'll try to remember everything....
so I have a **Notebook:** Asus Eee PC 1008P
**Processor:** [Intel Atom N450]("http://www.notebookcheck.net/Intel-Atom-N450-Notebook-Processor.23722.0.html")
**Graphics Adapter:** [Intel Graphics Media Accelerator (GMA) 3150]("http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-3150.23264.0.html") and installed ubuntu on it, which was amazing at first, great speed, good battery life (the battery is only a few months old and first was giving me 3.5-4 hours of autonomy when fully charged, but then all my fonts and buttons became large, too large to be confortable and I changed to Xubuntu. Since then the battery is giving me 1 hour and 5 minutes of autonomy when fully charged and while I was testing Kubuntu in live mode, I got a message that said that my battery might be broken and that it's only at 36% of capacity at full charge...
I checked the battery in terminal and it said the same thing...
What is happening???
Can it be that it comes from a driver problem or something, because I read on the forums that sometimes linux uses 2 drivers for the graphics card or something and that that drains the battery a lot faster, but then why didn't it happen since the begining?
I would understand that an old battery would give an hour of autonomy, but this is brand new and I had 3hrs plus just a few days ago!

Please help me find a solution

---

### Post by TheFu on 2015-04-02
That's an old Eee. Batteries go bad over time and hold less charge. About a yr ago, I switched from an Asus Eee 1008H to a $199 chromebook and I'm mostly happier (besides the damn keyboard) running 14.04.  My Eee battery life was never very good, but I wasn't the original owner.

It may be possible to get a replacement battery for Eee. I dunno, but I've been burned with after market batteries almost always.

---

### Post by banchshee on 2015-04-02
You mean that it's normal that a battery which I bought new on Christmas on ebay is charging only at 36% of it's capacity when full?
I really had 3hrs plus just a few days ago and I found some other people having the same issues...
but now, even when I boot something in live mode from the usb, the time stays the same, around 50% of the battery it starts telling me that it will shut down...
could it be that something has installed itsellf in the Bios?

Hope it's not the national security agency who drains my battery :)

---

### Post by TheFu on 2015-04-02
> **banchshee said:**
> You mean that it's normal that a battery which I bought new on Christmas on ebay is charging only at 36% of it's capacity when full?
I really had 3hrs plus just a few days ago and I found some other people having the same issues...
but now, even when I boot something in live mode from the usb, the time stays the same, around 50% of the battery it starts telling me that it will shut down...
could it be that something has installed itsellf in the Bios?

Hope it's not the national security agency who drains my battery :)

If it happened recently and in a major changed-way, check your power settings. Especially the brightness for the LCD and the length of time before it dims and powers off.  Also check that atime isn't enabled on spinning disks.

Found a few links:
* [https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
* [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)
You've probably already checked those before posting. Meant for lurkers.

I don't buy anything from ebay - might be a personal issue.  Cheap things usually have a reason for being cheap, IME.

**Batteries**
I've been burned buying batteries at radio shack, amazon, and a few other online retailers. Usually the exact OEM battery wasn't available and settling for a "close replacement" didn't provide the same performance.  With some, the batteries were still shrink wrapped, with holograms and only lasted about 8 months before dropping to 50% levels.

The only place that worked well was for replacement APC batteries for a few UPSes - they were expensive - and it was a battery replacement specialty e-tailer. 4 yrs later and those batteries are still working as expected. Zero issues. They don't sell normal batteries - just batteries for UPSes.

Was forced to buy some L-Ion batteries for a smartphone - Nokia wanted $95 - Staples had something close (20% smaller) for $22. Got 3.  These didn't last as long (expected) per charge and after 14 months of use, would only hold 50% of the rated charge - about a 3 hr use per battery.  Swapping a battery in a smartphone every 3 hrs sucked, but for international flights back then, it was the only choice (no seat power).

I'd guess it is a setting change, not the battery at this stage - maybe 10% chance it is the battery.

Doubtful that any BIOS changes happened, unles the BIOS battery died. That should be easy to replace, assuming the Eee actually uses a CMOS battery. My chromebook doesn't - it uses the normal, main, battery, so if that discharges completely, all BIOS settings are lost.  Google found this [http://www.youtube.com/watch?v=pIyLFF8x0Mk](http://www.youtube.com/watch?v=pIyLFF8x0Mk) - looks like there is a CMOS battery for your Eee.

Sorry I'm not more help.

---

### Post by banchshee on 2015-04-08
Thank you for your answers, will check out about that CMOS battery Now the battery? or the computer is making like a noise, as if a disk or something was trying to rotate, then stops, then again, like that every 2 seconds. Even when the computer is turned off and charging. Yesterday I charged it while not turning it on and this morning when I turned it on, there was only 30% battery left, so I guess the problem comes from the CMOS battery, because I only get 16minutes with 60% of battery now...  Thank you all

---

