---
title: "My Compaq Preasario v2000 Battery..."
date: 2008-05-04
forum: Hardware
---

### Post by DonnyB4e56 on 2008-05-04
I don't know if it is Ubuntu or my battery, it's not showing up in the top right it says "Unable to get data..." So if anybody could give me a hand with their past experiences or solutions I would be very grateful.


Thanks, Donny.

---

### Post by biophysics on 2008-05-04
Before doing anything below can you post: 
ls  -lR /proc/acpi/battery/

Then
Check if there are any settings in BIOS like "Battery calibration" or equivalent try doing that. Otherwise shutdown the machine and remove battery. Then boot the machine without battery and see what is the error message. wait for a few hours and reinsert the battery and see what happens.

---

