---
title: "HP 6910p: Fan going crazy on 12.04, unlike on Windows; &quot;No proprietary drivers&quot;"
date: 2014-07-13
forum: Hardware
---

### Post by bY4D6sE on 2014-07-13
I have  HP 6910p laptop which runs smoothly on Windows XP. However on Ubuntu 12.04 the fan is working non-stop and the laptop seems to overheat.

Some suggestions I found around the web were either to install Jupiter and change the power options or to install Proprietary drivers, however Jupiter has been discontinued and when I try to install the proprietary drivers I get the message that "no proprietary drivers are in use on this system".

All suggestion for solving the "no proprietary drivers" message seem to be aimed at the users with nVidia graphic cards, but I have AMD's Mobility Radeon X2300.

The system is fully updated.

---

### Post by Vladlenin5000 on 2014-07-13
Your graphics card is fully supported by the open source driver but it's too old to run the standard Ubuntu's desktop environment, Unity.
Your options are Xubuntu, Lubuntu or any other lightweight flavor/distro.

---

### Post by Mark Phelps on 2014-07-13
> I have AMD's Mobility Radeon X2300.

Sorry, but AMD dropped Linux driver support for the X-series cards YEARS ago; thus today, the only drivers are the default open-source Radeon drivers.

---

### Post by Yellow Pasque on 2014-07-13
The open-source radeon driver's dynamic power management has come a long way since 12.04.
I would try a Live USB of 14.04 and see if the fan still runs too much at idle.

> but it's too old to run the standard Ubuntu's desktop environment, Unity.
I'm pretty sure the X2300 supports all features needed to run fully-accelerated Unity.

---

### Post by Vladlenin5000 on 2014-07-13
Yes, you're probably right according to this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by coldraven on 2014-07-14
At the login select 2D mode and see if it runs cooler.
I'm running 14.04 on a HP 6715b with the ATI X1250 card and it works for me.
On second thoughts the 2D mode might not be available on 12.04. In which case Xubuntu would be a good choice.
Either way 3D games or effects will be no good :(

---

