---
title: "Low NIC Speed : what is the bottle neck ??"
date: 2011-09-19
forum: Hardware
---

### Post by roy.nico on 2011-09-19
Hello Community, 

Here is the problem i'm facing since many weeks : I'm trying to get gigabit at home !
I have a laptop HP touchsmart Tm2 2105, with is equiped with a NIC with chipset from Realtek r8168. It is well known that out of the box, the driver r8169 would be used. 
* But i installed the newest driver from Realtek website. The driver is installed and loaded. 
* ethtools indicates a speed of 1000Mbps
* but if i perform a simple download test (filezilla) with a desktop PC under windows (direct connection with cat6 cable), i only reach 130 Mbps
* The same test, with the laptop booted on windows shows app 500 Mbps
Just to be sure, i tested the speed of the HD of the laptop : "1700 MBbs"  and "80 MBps", which is more than reasonable.

Where could be the problem ? 

Notice, that i tested also with another Desktop PC under Ubuntu Lucid. I tried several gigabit PCI cards (at least 3) -> always the same story : the driver is correctly installed, ethtools indicates 1000 Mbps, but the actual rate is app. 100 - 130 Mbps.

Did anybody ever manage to have Gigabit rates under Ubuntu ?!

nicolas

---

