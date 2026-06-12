---
title: "ROG STRIX B760-I GAMING WIFI compatibility"
date: 2024-04-21
forum: Hardware
---

### Post by tom3f on 2024-04-21
[COLOR=#353C41][FONT=Inter]Hello, I would like to build new PC as my Pentium G4500 has not enough performance. Since I am Linux only user I need new hardware to be compatible with at least latest distributions. My primary use-case is programming, virtualization, docker and similar.  I am not interested in overclocking or gaming.[/FONT][/COLOR]
[COLOR=#353C41][FONT=Inter]
Does anybody have experience with this motherboard ?[/FONT][/COLOR]
[COLOR=#353C41][FONT=Inter]ROG STRIX B760-I GAMING WIFI [https://rog.asus.com/motherboards/rog-strix/rog-strix-b760-i-gaming-wifi-model/](https://rog.asus.com/motherboards/rog-strix/rog-strix-b760-i-gaming-wifi-model/)[/FONT][/COLOR]
[COLOR=#353C41][FONT=Inter]Together with:[/FONT][/COLOR]

[LIST]
[*]CPU: i5-14500
[*]Memory: Kingston FURY 32GB KIT DDR5 4800MHz CL38 Beast Black (KF548C38BBK2-32)
[*]SSD: WD BLACK SN850X NVMe 1 TB
[/LIST]
[COLOR=#353C41][FONT=Inter]
I need at least LAN, SoundCard, USB and USB-C ports, Integrated GPU, M2 ssd to work perfectly with no performance penalty.[/FONT][/COLOR]
[COLOR=#353C41][FONT=Inter]Wifi and bluetooth is not needed but it would be nice if it works too. Until now I only found single compatibility report online which was not great but it was more than six months old. I will be using only latest linux so I need compatibility with Ubuntu 24.04 LTS / 23.04. Can anybody help me figure out if this motherboard will work ?[/FONT][/COLOR]
[COLOR=#353C41][FONT=Inter]
Thank you.[/FONT][/COLOR]

---

### Post by him610 on 2024-04-21
> my Pentium G4500 has not enough performance
You might consider just upgrading your CPU to one of the same generation.
[https://www.ebay.com/itm/386886649320?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=386886649320&targetid=2295557532670&device=c&mktype=pla&googleloc=9006731&poi=&campaignid=20387609897&mkgroupid=161160433637&rlsatarget=pla-2295557532670&abcId=9316960&merchantid=6296724&gad_source=1&gclid=Cj0KCQjw8pKxBhD_ARIsAPrG45mfXIWtGmmD1tHc-U6wIKRbsmV385ygE286kR7lXojgJWjn4j1hVcsaAk75EALw_wcB]("https://www.ebay.com/itm/386886649320?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=386886649320&targetid=2295557532670&device=c&mktype=pla&googleloc=9006731&poi=&campaignid=20387609897&mkgroupid=161160433637&rlsatarget=pla-2295557532670&abcId=9316960&merchantid=6296724&gad_source=1&gclid=Cj0KCQjw8pKxBhD_ARIsAPrG45mfXIWtGmmD1tHc-U6wIKRbsmV385ygE286kR7lXojgJWjn4j1hVcsaAk75EALw_wcB")
With an upgraded CPU, you would be able to reuse your existing motherboard and memory. 
For only $50, it might be worth it.

---

### Post by tom3f on 2024-04-21
Thanks for tip but i have more reasons to upgrade than just CPU.

---

### Post by tom3f on 2024-04-27
Hello so I can happily report that it works just fine with Ubuntu 24.04 LTS.



Sound: Works (Tested Line out for headphones)
Wifi: Works (I see low link speed only around 250Mb/s sometime jumps to 750Mb/s, router is capable of 867 Mbit/s)
Bluetooth: Works (tried bluetooth mouse)

Ethernet: Works (tried 1 gigabit)

iGPU: Works great

Overall performance is good, lm-sensors can recognize temperatures

---

