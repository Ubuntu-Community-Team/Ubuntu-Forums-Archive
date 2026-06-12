---
title: "TV Tuner Card Sound Not Working"
date: 2009-10-01
forum: Hardware
---

### Post by ashishWaghmare on 2009-10-01
Hi, 
 I have new Desktop x64 bit hardware. Also old Frontech TV Tuner Card.

Sound for TV tuner card comes as Input source. But mic is not working in Ubuntu 9.04.

Same setup worked in Fedora 11 with no issues.

I dont know what is wrong with my installation or with Pulse Audio

Somebody Please Help !!

------------------------
got the issue resolved . Since Windows detects jackin dynamically but somehow linux hardcodes the input ports
so configurtation of Cables/jackin which worked well in Windows 7 beta dint worked in linux. 
Even fedora 11 detected my 3.5mm jackins in a different way.
...
Tried permuation and combination for Jack- ins..
It worked perfectly.


Thanks

---

