---
title: "[SOLVED] Clock running too fast when Speedstep enabled"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Colonel Kilkenny on 2007-08-23
Hi,
I'm wondering if anyone has had the same problem. 
So, I'm not an expert with this kind of hardware & software related problem, but I guess that the problem is this:
If speedstep is enabled from BIOS and nothing too CPU-intensive is done with the computer Feisty tries to lower power consumption with dropping both cores from 1800MHz to 1200MHz. And when the clocks are at 1200MHz the clock (time) starts running too fast.
Speedstep disabled everything is working just fine. 

This is desktop computer so the whole speedstep thing isn't a must-thing to have but it would be nice if I'd somehow get it working properly with clock.

I've tried to Google and search for forums but with no luck. There are problems and bugs similar to this one but most of them aren't related to speedstep (I guess).
The next stop I guess would be to update BIOS but I wouldn't want to break this whole damn thing :)

Specs:
Intel Core 2 Duo processor (E4300)
Asus P5B -motherboard
Not too many months old so it's not a battery problem.

edit. I've also tried booting with things like notsc (Feisty doesn't start), acpi=off etc.

edit. BIOS-update did the trick. Now clock works normally even with speedstep enabled.

---

### Post by dryliketoast on 2008-03-28
thanks for posting your findings - i'm having the exact same issue. i also have the same mobo as u

---

### Post by shirsch on 2008-04-30
Ok, same motherboard and latest BIOS flash.  Still runs fast.  Anyone have a guess as to how to remedy this?

What I cannot understand is why ntp is not able to correct it dynamically.

---

