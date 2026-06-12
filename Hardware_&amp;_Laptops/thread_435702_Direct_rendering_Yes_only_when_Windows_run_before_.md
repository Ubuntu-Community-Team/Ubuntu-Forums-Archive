---
title: "Direct rendering: Yes only when Windows run before Ubuntu"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by UNKpl on 2007-05-07
I have weird problem with Ubuntu and my graphic card :(

My computer: Asus K8N-E + AMD Sempron 3000+ + Radeon Sapphire 9550 ( i think is most need information )

Problem like topic name. when i boot Linux i don't have Direct rendering, when compiz/beryl is on i have blank screen. All work but i don't see anything. If i first boot Windows and reboot to Linux i don't have any problem, Direct rendering: Yes and all work great.



PS. Sorry for my weak English ;)


EDIT: @down: i have too problem with Eth. but not always i could turn off and on my connection and all work fine ;) ( Asus K8N-E with integrated NIC )

---

### Post by ahaslam on 2007-05-07
Sounds more like a possible psu problem to me. My Ethernet never starts after a power down, though it's fine after a reboot :rolleyes:

---

### Post by teaker1s on 2007-05-07
it sounds like the direct rendering component of the windows driver stays active in graphics card ram.
I would suggest shut down and power off-then seek assistance with direct rendering in linux.:popcorn:

---

### Post by UNKpl on 2007-05-07
I always turn off my PC ( also from power soruce ) at night. I install Linux when first boot PC and have problem with DRI on open and close driver ( and this trick working only when i have installed open driver ).

---

### Post by teaker1s on 2007-05-07
sometimes devices such as lan can have power in a turned off state (example lan ring) shut down and unplug to be sure the ram powers down

---

### Post by UNKpl on 2007-05-09
nothing :(
turn off pc - unplug VGA card - turn on - turn off - plug VGA card - and boot Linux - reinstall mesa-dri and install fglrx driver and: Direct rendering: No :(


On polish board someone ask my that i use other driver for windows ( like omega ) and atitray tool, maybe this have some effect on VGA card ( but i don't change anything in atitray tool ).


EDIT: I also reinstall Ubuntu ( 7.04 ) to free formatted partition without boot Windows XP and still white screen :(
Problem with connection to Internet disappears.

---

