---
title: "Hibernation wont work with irqfixup boot option"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by shadowhywind on 2007-08-14
Hi all, having an issue with hibernation/Suspend Hopefully someone can help. The issue:
  When ever i try to hibernate it locks the screen, goes to black, and then goes right back to the screensaver. 
When i try to use s2disk it goes to a black screen and just hangs there. 

However there is good news. 
s2disk works perfectly great if i remove irqfixup from the boot list. 
But if i remove irqfixup and leave my computer alone for say 5 minuets, everything is jumpy

So any solutions to eather s2disk or how to remove irqfixup

---

### Post by shadowhywind on 2007-08-15
Messing around with things last night, *with high chances of breakage*, i fixed my issue. I changed irqfixup to be irqpoll. So far all signs are looking good. Hibernate works, computer doesn't freeze after being idle, and haven't ran across any other issues yet. So hopefully this might help someone down the road.

---

