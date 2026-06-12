---
title: "Why should things stop working with Dapper?"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by arthur on 2006-06-07
Might sound a bit naive, but not to me :p 
Assume 90 out of a max. of 100 things work on a certain laptop under Breezy.
After upgrading to Dapper on the SAME LAPTOP, the number of things working should in theory be at the very least 90 again.

My question:
Any logical explanation for the number to go under 90 with Dapper?
I am not trying to be sarcastic, seriously, but I understand that once a certain degree of functionality is achieved with anything, newer software releases only improve that functionality, they are certainly not supposed to reduce it. :-k

---

### Post by Jussi Kukkonen on 2006-06-07
Operating systems are complex beasts -- when one part is changed (to fix a bug or implement a new feature), the changes might lead to another, seemingly unrelated, bug. 

The worst part is that operating systems are used on millions of different hardware+software combinations -- If we want to ensure that no new bugs are introduced, we need to test the new code on all those combinations... You probably found a new bug on a yet untested combination.

In short: code will always have bugs. If you add more code, you risk adding more bugs.

---

### Post by Augi on 2006-06-07
I understand your feelings arthur, under 5.04 my laptop was fully functional. 5.10 I couldn't even get the graphical installer to load properly, now with 6.06 (Dapper) everything minus the ACPI is working. 

Round and round and round we go. Woosh.

Regards,

Augi

---

