---
title: "Battery monitor not working [10.04 on Fujitsu V6555]"
date: 2010-05-28
forum: Hardware
---

### Post by srulop on 2010-05-28
Hi,
The problem is that the battery monitor shows that the battery is fully charged when the AC adapter is unplugged and it is in fact discharging. When I open the Power Statistics window, I can see that the discharging data is correct, though in "State" line it's still written "Fully Charged", while it's only 6.3% charged.(See attached image). The history graph is OK as well. When _charging_ - all is correct (the data as well as the panel icon).

Pic. 1: The Power Statistics window while discharging
[IMG]http://img3.imageshack.us/img3/9529/screenshothn.png[/IMG]

Pic. 2: The charge history plot while discharging
[IMG]http://img249.imageshack.us/img249/5569/screenshot1pn.png[/IMG]

Pic. 3: The Power Statistics window while charging
[IMG]http://img686.imageshack.us/img686/4277/screenshot2su.png[/IMG]

Any solutions?
Thanks!

---

### Post by srulop on 2010-05-30
Help? Anyone?

And how do I submit official bug report about this? Because it's clearly a bug.

---

### Post by Cerin on 2010-06-01
At least you get a battery monitor. I'm not seeing one at all...

---

### Post by srulop on 2010-06-03
Haven't anyone found solution to this? It seems very simple - the graph already shows the correct percentage, but only transmits to the monitor that the battery is full. It should be that every time it sees that the battery is discharging (as it does) it should write "battery discharging". Seems like just a couple of lines of code... I'd fix it myself, but I don't really know how. I'm good in programming in Maple (math software), but have no idea how Linux is built...

---

### Post by srulop on 2010-06-03
Just compiled and installed the latest Gnome power manager (2.31.1) - didn't help, only the brightness control disapeared. This Gnome power manager is very buggy - in the old one the brightness control didn't work properly as well. My only problem with Ubuntu is this power manager! Makes me mad!

Also, I can hear the hard disk actuator beating against something very often when on battery or charging - I think it has something to do with the power manager also - the disk tries to spin down. I marked "spin down when possible" on battery AND on AC power, but it just spins down when it feels that the battery is charging or discharging.

Conclusion: Gnome power manager is very buggy. How come no one fixes it??

---

### Post by Starpoint on 2010-07-13
I have a Dell D830 running Ultimate Edition Ubuntu 10.04 GAMERS  (all the multimedia stuff and software) and on my Dell, the battery will last about 2.5 hours but if I check the battery meter icon, it will show 1.5 hours then 1 minute later show 2 hours, and 3-4 minutes later show 1 hr 20 minutes later. 

After about 2 hours the laptop will just shut down, no warning, just OFF.

any ideas?

---

