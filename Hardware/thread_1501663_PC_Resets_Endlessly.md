---
title: "PC Resets Endlessly"
date: 2010-06-04
forum: Hardware
---

### Post by NukeouT on 2010-06-04
Installed Ubuntu somehow. A lot of the time the machine will go into restart loop.

This seems to be a hardware thing between the mobo and case.

I have a 2001-2003 Antec case
and the Intel D845GEBV2 478 mobo

at first when I started working with it I could not find the pin instructions so just flipping power switch to ON with cable IN would start the machine. Later it developed that "restart after several seconds no matter what" symptom. Yesterday I found the directions which say- 

pins are like this
::::.

:_:_:_:_.
4 3 2 1 ?

then there is a label below that indicating
1 power
2 restart
3 pwr led
4 hdd led

text is oriented with directions torwards 4 as up and torwards 1 as down.

Yesturday everything worked, today that same configuration does not work. Plugging power into the 1 power, with text up without affecting the rogue (.) pin does not do anything. Plugging into reset turns on the computer, and plugging restart into restart turns on the computer. How ever doing it with restart puts it in that "restart loop", while putting it into power does nothing.

I dont know what to do, and I dont know why power in power and reset in reset works only sometimes. I also dont get why it sometimes is able to start through power switch with nothing plugged into mobo from case.

---

