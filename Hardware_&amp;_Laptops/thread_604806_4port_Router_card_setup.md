---
title: "4port Router card setup"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by PanzerMKZ on 2007-11-06
I have this realtek chipset 4port router card.  

[http://www.geeks.com/details.asp?invtid=A-3905&cat=NET](http://www.geeks.com/details.asp?invtid=A-3905&cat=NET)


shows up as eth1 on my box but don't know what I need to do to make the other ports working.  when I try to get a ip address via dhcp it errors out saying eth2 and eth3 no device found.


Thanks
Panzer

---

### Post by netbandit on 2007-11-06
Wow... what an interesting card.

For $13 bucks, I would bet that this is just a quad Ethernet card, and has no on board routing ability.  I would guess that it uses software to have the OS do the routing.  This is not necessarily bad, but it does mean that you have to do the legwork... probably using iptables, etc.

> it errors out saying eth2 and eth3 no device found

Check to see if the ports of the 4port network card are bridged.  try using it like you would use a switch.

-nb

---

### Post by PanzerMKZ on 2007-11-19
Yea lt looks like they are bridged.   I can plug in one cable and swap around to different ports and I get the same eith1 on all of them.


Panzer

---

