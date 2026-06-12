---
title: "Problem with wifi on HP Pavilion on Jaunty"
date: 2009-06-13
forum: Hardware
---

### Post by EngineerScotty on 2009-06-13
I just installed Jaunty on a HP dv6809us (Pavilion) laptop--things went fine except for--you guessed it--wireless.  Machine has an AMD x64 processor, 3Gb RAM, installed 64-bit desktop edition. Came with Windows Vista (eww) on it; Vista is still present and functional.  Wireless is a Broadcom chipset, not sure exactly which chip.

Except the issue I'm having seems a bit different than the numerous does-not-work-at-all reports I've seen here and elsewhere.

The wireless starts out working, then continually drops out, and is FTMP unusable.  Laptop is sitting literally inches from the router, and works fine when Vista is booted.  (Other than it runs like a pig...)

What's more--when I plug in an Ethernet connection--THAT drops out from time to time.  Especially, it seems, when I'm trying to install updates to the system. 

I've tried both the B43 driver and the newer driver that comes with Jaunty; the B43 driver isn't working at all; the other driver produces the behavior above.

Anyone heard of this behavior before?

---

### Post by EngineerScotty on 2009-06-14
Update--the Ethernet issues were a bad cable; swapping cables solved that problem.  Wireless still is not working.

---

### Post by EngineerScotty on 2009-06-14
Seems to be working now, though with a non-free solution.

Diving deeper into the linuxwireless docs, I determined that the specific chip is a Broadcom 4312-low power chip; which the B43 driver does not (currently) support. Going to broadcom's website, I noticed that the (non-free) STA driver had been rev'd since Jaunty was released.  I downloaded and built the latest rev of the STA driver, installed it, and the wireless now works.
Still slow... but the connection is slow on Vista as well.

---

### Post by Bucky Ball on 2009-06-14
Do you have ubuntu-restricted-extras installed?

What have you got in:

System->Administration->Hardware Drivers

 ?

---

### Post by irv on 2009-06-14
Just for a comparison here is what mind looks like:
[ATTACH]117671[/ATTACH] 
But I have a Dell Inspiron 1521.
One more thing, I got rid of the Gnome Network Manager and when with wicd Network Manager, and I find it works and hold connections very well.
Here is what the wicd manager looks like on my machine:
[ATTACH]117672[/ATTACH]

---

