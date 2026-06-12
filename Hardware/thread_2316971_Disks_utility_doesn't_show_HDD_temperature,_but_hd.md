---
title: "Disks utility doesn't show HDD temperature, but hddtemp does"
date: 2016-03-12
forum: Hardware
---

### Post by james204 on 2016-03-12
Hi,

I have 2 HDD's in my machine. One shows with a temperature under the "assessment" title of the Disks utility, and the other shows just "Disk is OK" (no temperature is reported).

The disk concerned is:
WDC WD5003ABYX-18WERA0 (0 1.01S03)

If I use hddtemp (sudo hddtemp /dev/sdb), it shows a temperature for this disk. Testing with GSmartControl, it shows the same temperature under Smart field 194, as you would expect. The disk passes a Smart test with no errors.

Is this something I can fix, or is this a bug?


Context:
If you're wondering why I care... it's because PSensor won't detect the temperature of this second drive, and I'm imagining it is because the OS doesn't recognise a temperature for the drive.

Any help would be much appreciated.


James

---

