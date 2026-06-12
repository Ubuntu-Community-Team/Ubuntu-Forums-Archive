---
title: "Very Slow Computer, Regardless of OS"
date: 2011-08-02
forum: Hardware
---

### Post by jpulec on 2011-08-02
This has been driving me crazy and I don't know where else to turn. I have PC dual booting Ubuntu 11.04 and Windows 7. I never had any problems with it for over a year, and recently decided to do a little partitioning and formatting to clean it out. After, I installed Win7 and then Ubuntu 11.04 everything was pretty much fine. I started noticing that every once in awhile Firefox or Rhythmbox would freeze and return after a few minutes for seemingly no reason. Then it seemed to happen with all my applications, and got to the point where it was unbearable so I just decided I would reinstall Ubuntu and hope that fixed it. Well, I tried running a LiveCD to do an install and it was taking ages (hours) to do anything. I then booted into Windows and noticed that it was also ridiculously slow. I do not have hardware that should be doing this (specs below). I don't know if something is broken or fried, but I cannot figure out what the issue is. I already ran MemTest86+ for over 4 hours and it didn't find any errors. Please help.


SPECS:

*Gigabyte* GA-X58A-[I]UD3R
Core i7 930 (4 cores clocked at 2.8Ghz)
6 GB Kingston Ram (3 x 2GB)
Seagate 7200 RPM 750GB Barracuda (Sata)
WD 5000 RPM 1TB (Sata)
MSI R5850 Twin Frozer II (ATI Radeon HD 5850)

Both Windows 7 and Ubuntu were 64-bit versions
[/I]

---

### Post by Beacon11 on 2011-08-03
Huh... yeah you really should be fine. You say it was running fine before you installed 11.04 and 7? What were you previously running? Have you run a hard drive diagnostic? (e.g. SMART)

---

### Post by jpulec on 2011-08-03
I was dual booting Win7 and 11.04. Before it became unbearably slow, I did run a SMART on both drives, and neither seemed to have any issues. What really concerns me though, is that it was still very slow when booting from a LiveCD, which doesn't involve the hard rives at all.

---

### Post by Beacon11 on 2011-08-03
Wait... so you had Windows 7 and Ubuntu 11.04 for some period of time and it worked fine. Then you decided to reinstall both and it's no longer working fine. Is that correct?

Every LiveCD I've used is super slow, I wouldn't worry about that. It might be faster if you put it on the flash drive instead of a CD though.

---

### Post by jpulec on 2011-08-03
That is correct. And I know that LiveCDs are slow, but I mean REALLY slow. Like it sat at the Ubuntu loading screen for about an hour before I got too frustrated and shut it off. Even my Grub is slow to load, though. The screen will turn purple, and then it will take another minute or two to display OS choices.

---

### Post by tgalati4 on 2011-08-03
Modern CPU's have thermal throttling.  So it's possible that the heat sink is dirty, or the paste is dried out, or the connecting hardware is cracked so you don't have a tight seal to the heatsink.

That would explain why the LiveCD is running slow as well.  It could also be a motherboard problem--the bus is waiting for data.

Run the LiveCD, open a terminal:

dmesg | tail -f

Wait for any interesting messages to pop up.  (Control-C to quit).

---

### Post by dilrukrocks on 2011-08-04
Why don't u try removing all the hard drives and booting Ubuntu from a USB...I had a similar problem sometime back and it turned out to be a bad pin on one of the hard drives.

---

### Post by Beacon11 on 2011-08-04
I like tgalati4's suggestion. Might want to check temps in the BIOS too. Let us know what you find!

---

### Post by walt.smith1960 on 2011-08-04
> **dilrukrocks said:**
> Why don't u try removing all the hard drives and booting Ubuntu from a USB...I had a similar problem sometime back and it turned out to be a bad pin on one of the hard drives.


This is a good thought. i had a situation where it acted like Windows had some sort of malware.  It was actually a bad IDE cable.  A basic install that was working properly, that same basic install was restored and now it's misbehaving?  That does sound sorta like a hardware problem.  It might be worthwhile to run memtest found on the liveCD too just to eliminate failing memory chips.  Let memtest run for a couple hours at least unless it shows errors before then.

---

