---
title: "TravelMate 8100 and ati x700"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by Njk00 on 2007-03-28
Hi all I have a travelmate 8100 with ati x700 card.
When I try to install ubuntu 6.10 the screen goes black when the cd launch gnome (I listen the song).
So i try the safe mode but it still not work. So I use the following argument in boot "linux vga=771 acpi=off pnpbios=off irqpoll". The screen is still black but i can switch to console and some users told me to modify xorg.conf by adding the string: 
Option "MonitorLayout" "LVDS,AUTO" 
in section monitor. So I make this and I save the file... Then I reboot but the problem remain...
Please help me!!

---

