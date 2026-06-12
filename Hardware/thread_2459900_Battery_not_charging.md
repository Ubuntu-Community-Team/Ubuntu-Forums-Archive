---
title: "Battery not charging"
date: 2021-03-29
forum: Hardware
---

### Post by Disabled20241022 on 2021-03-29
I have had this laptop for lot of years (HP Pavillion 17) and a year ago i used to be on windows and i had the same problem, bought a new battery and it worked for a few months and then back to the same problem.
I keep am required to keep my charger in the laptop or else it will go off.
In the past it showed 60% constinuesly and this year only 4%, today it turned off because the cable went out of the socket a little bit, it wen from 4% to 0%.
The thing has been off and charging for the entire night.

What am i to do?

---

### Post by Disabled20241022 on 2021-03-29
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```
 native-path: BAT0 vendor: Hewlett-Packard
model: Primary
power supply: yes
updated: ma 29 mrt 2021 12:24:56 CEST (92 seconds ago)
has history: yes
has statistics: yes
battery
present: yes
rechargeable: yes
state: charging
warning-level: none
energy: 0 Wh
energy-empty: 0 Wh
energy-full: 36,288 Wh
energy-full-design: 36,288 Wh
energy-rate: 0 W
voltage: 10,242 V
percentage: 0%
capacity: 100%
technology: lithium-ion
icon-name: 'battery-caution-charging-symbolic'
```

---

### Post by Autodave on 2021-03-29
Sounds like a defective battery to me.  Did you buy it from HP or aftermarket?  I have had great luck with some aftermarket batteries and horrible luck with others.  Understand that the aftermarket batteries are not normally "new" but rather made of parts from failed batteries.

---

### Post by Disabled20241022 on 2021-03-29
The laptop was from HP and then years later i replaced it from a marketplace. both did the same thing.

---

### Post by Autodave on 2021-03-29
Aftermarket batteries have always been a problem.  And, the cheaper the battery the more numerous the problems.  I have 2 HP laptops here and several in other people's hands.  Never had a problem with Linux on them or with HP batteries.  2 of them have aftermarket batteries and both of them have issues.

---

### Post by CelticWarrior on 2021-03-29
> **Autodave said:**
> Aftermarket batteries have always been a problem.  And, the cheaper the battery the more numerous the problems.  I have 2 HP laptops here and several in other people's hands.  Never had a problem with Linux on them or with HP batteries.  2 of them have aftermarket batteries and both of them have issues.

This ^^^
If you still have Windows installed how does it behave with it? If it's the same then obviously hardware is to blame.

---

### Post by Disabled20241022 on 2021-03-29
I do not have windows, but for years this problem was on windows 10 also.

Right now i have my laptop charged for a couple of days but the battery says 0%, if i remove the cable in a few minutes it shuts down.

---

### Post by Autodave on 2021-03-30
You need to start with a new battery: from HP or at least some company known to sell good ones.  If in doubt, buy HP.

---

