---
title: "Faulty DC jack and weird messages from Power Manager"
date: 2009-09-08
forum: Hardware
---

### Post by valmi on 2009-09-08
I made the mistake of buying an HP laptop and now I'm stuck with a faulty DC jack (I think). I'm going to try and fix this as soon as I can get the part, but in the meanwhile I thought the funny and contradictory messages I get from GNOME Power Manager (2.24.2 running on Ubuntu 9.04 with Xfce 4.6.0, kernel 2.6.28-15-generic) could help me understand the nature of the problem before I even open the damn thing.

This is the situation that occurs most often: the adapter is plugged in and the power is going at least as far as the jack since the LED next to it is lit, but obviously the power is not going to the board because the 'charging' LED is off and the the battery is discharging. But here is where it gets fun:
[IMG]http://valmi.info/img/battery.png[/IMG]

Power Manager knows that I'm running on battery power, but somehow it also knows that there is power coming down the mains. I suppose this is why it gets confused and thinks that the battery is full. This suggests to me that the jack or its connection to the board is not simply 'broken', and I thought that someone that knows better than me how computers, the kernel, and/or Power Manager work would be able to figure from this information what exactly is wrong with the computer.

Here's another contradictory message I get from Power Manager, but I can't see any logic in this one...
[IMG]http://valmi.info/img/ac-discharging.png[/IMG]

Thanks for your help!

---

