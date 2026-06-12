---
title: "Poor resolution after upgrade - Intel card"
date: 2012-06-09
forum: Hardware
---

### Post by KG1980 on 2012-06-09
I am only been able to run my Dell 1012 at 800x600 resolution.  It should be able to run at 1024 x600.

 I've tried changing the resolution via the settings menu but 800x 600 is the maximum possible.

My graphics card is an Intel 3150.   When I type in lspci -nn | grep VGA I get:

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]

In "additional drivers" no option comes up.

This has been a problem since I upgraded to 11.10, though I have since upgraded to 12.04.  I have had problems with at least these packages since the upgrade:

lightdm (I think I'm currently using gdm)
bluez
colord
whoopsie

installArchives() failed

I had no problems prior to 11.10.

I'm a non-technical user, so please keep any answers simple!

Many thanks

---

