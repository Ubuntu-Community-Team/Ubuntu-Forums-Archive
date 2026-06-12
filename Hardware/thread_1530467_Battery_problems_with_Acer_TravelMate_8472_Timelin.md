---
title: "Battery problems with Acer TravelMate 8472 Timeline X"
date: 2010-07-13
forum: Hardware
---

### Post by traveljenny on 2010-07-13
Heya,

I just bought the Laptop Acer TravelMate 8472 Timeline X and installed Ubuntu 10.04 on it.
I have an issue with the battery recognition. Tried to find a solution, but haven't gotten
very far... Tried also Ubuntu 9.10, but same issue there.

The problem:
The battery indicator always shows "plugged in", even if it
is not. I guess it is an ACPI error, and the battery is not 
even recognized:

dmesg | grep battery

returns

[    0.623092] ACPI: Battery Slot [BAT1] (battery absent)

I only found a few threads with people mentioning the same 
problem, but I found no solution. 

Anyone had the same problem and found a solution?

Help much appreciated :)

Cheers
Jenny

---

### Post by lazerradial2003 on 2010-07-17
Also looking for a solution to this but no real progress yet, any luck?

For me dmesg | grep battery shows this:

[    0.684203] ACPI: Battery Slot [BAT1] (battery present)

so the battery is at least detected but charge level etc is unavailable

---

### Post by traveljenny on 2010-07-19
No, unfortunately no progress so far... I have it running on AC now, hoping that the problem resolves with a future update (hopefully soon). My guess is that acer-wmi (former package which has now been built into the kernel) might have to be updated. I tried to find out more, but no success - so now, I just have fingers crossed for future updates.
Please let me know if you have any progress!
 
Cheers
Jenny

---

### Post by traveljenny on 2010-07-22
I guess this issue is related to this thread:
[http://ubuntuforums.org/showthread.php?t=1495123](http://ubuntuforums.org/showthread.php?t=1495123)

---

### Post by h0nIg on 2010-12-31
update bios version to 1.2 to solve the problem

---

