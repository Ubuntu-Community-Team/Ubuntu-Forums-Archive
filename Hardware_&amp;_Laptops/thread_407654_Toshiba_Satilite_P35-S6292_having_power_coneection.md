---
title: "Toshiba Satilite P35-S6292 having power coneection trouble"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by Death_Sargent on 2007-04-12
On edgy my laptop for some reason will stop charging the battery and start using it for power while plugged in. 

The light that indicates it is plugged in is still lit up but the charging light is off. 

Ubuntu also indicates that it is using battery power and removing the battery confirms this. 

I have worked out what happens to measureable stages.

[LIST=1]
[*]First if it lasts all the way threw the boot then it will run for a bit.
[*]Then it will say my battery life is at 100% and has 6 minutes left
[*]Then the charging light turns off
[*]It will constantly make random estimates on how much time and energy is left for battery power.
[*]In time it will get it right (this occurs between 98% and 65% battery life)
[/LIST]

The only fix I have found is to roll up a small bit of electrical tape and place it in the socket with the laptop charging plug. 

This forces the plug to sit firmly on all the metal connectors. 

This was also never a problem under windows-XP or Vista.

It took allot of jiggling and replugging to make the problem occur when only the bios was running.

---

### Post by Death_Sargent on 2007-04-18
now it just seems to happen completely at random. 

also it will now randomly claim the battery is at 0 fooling even gkrellm which typically is more acurate than the system. 

please can some one help me

---

### Post by Zuph on 2007-04-18
Does the problem replicate itself under a liveCD or windows environment?

The most common explanation would be that the power connector in your laptop is going bad.  It's an extremely common problem being that the connector is a very high-wear part over the life of the laptop.

---

### Post by Death_Sargent on 2007-04-18
never happened under live cd nor windows.

infact it seems that when i reinstall or just install a new Os the problem leaves for a bit but not perminantly

---

### Post by Zuph on 2007-04-18
I mean, have you tested it recently under a livecd or another OS.  This is the sort of problem that could appear overnight as a result of too much wear, if the problem is actually the connector wearing out.

---

### Post by Death_Sargent on 2007-04-18
Yes i have.

---

