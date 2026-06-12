---
title: "Mini-9 - Suspend hangs with /home on SD Card"
date: 2008-12-14
forum: Hardware
---

### Post by Chareos on 2008-12-14
Hi guys,

I recently bought this beautiful netbook.
After a while, I decided to move from the 8.04.1 Hardy installed by Dell to Intrepid i386.

I got almost everything working, except
1- wifi timing out here and there 8both proprietary and non drivers)
2- suspend failing (with blinking cursor) if I use /home on a SD card.


About .2
I already tried not to use SD for /home, and everything works like a charm.
I read aroud that for Asus EEE someone created a kernel to make usb persistent. Is this the case/solution also for Dell/Intrepid ?
Or maybe that necessary support have been merged into Intrepid kernel by now ?


Anyone has suggestions to make it work ?


Thank you all in advance
Fabio

---

### Post by Chareos on 2008-12-17
Seems nobody so far.

So, tonight I'll try Check to see if adding the SD card reader module to the MODULES section of "acpi-support" is enough to fix this problem.

I'll keep you informed.

---

### Post by Wwiillburr on 2009-01-04
Anyone have any update on this problem.  I would like for suspend to work for me, but I also have /home on an SD card.

---

### Post by Chareos on 2009-01-06
I tried the acpi-support thing, but didn't work.

I'm going to file a bug:
- I should be able to move /home on SD to make it easily movable between different systems, or cause people suggests it may help SSD disks lifespan (?)
- it's just shocking I have to remember to unmount any ssd card before a suspend... containing /home or just photos, it's just shocking.

---

