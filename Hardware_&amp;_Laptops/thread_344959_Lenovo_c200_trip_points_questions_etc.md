---
title: "Lenovo c200 trip points questions etc"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by Michael_aust on 2007-01-23
Today I purchased a LLenovo 3000 c200 laptop.  Everything works great except for the sound.  But I knew about this already from reading some other peoples threads regarding the issue.

Anyway, While II was in windows the fan seemed to be running constantly, the same is true in Linux as well.  The fan runs almost silent, it barly noticable, unless you put your ear right next to the machine.

Anyway, would it be worth me messing around trying to get the fans to come on and off.  As yet I have not had the fan speed up more, or turn off, neither in Windows or Linux.  So I am guessing this is not abnormal given tht it happens in Windows.  I just seems to stay on.  (I do not have Windows instlled anymore, I created the recovery discs and then wiped the machine, but in the three hours Windows was running the fan seemed to be on all the time).  TThe fans have never increased, not even when installing Ubuntu and Suse, they just stayed on bit on low and quiet.

The machine does not feel particularaly hot, the fan vent is about the same temperature as your psu fan vent

Can any one help me with trip points and frequency scaling.  When I run these command , I get the following outputs:

cat /proc/acpi/thermal_zone/TZ00/temperature
 
 44 C
 
(I think my machiens normal operating temperature is 44 C so the fans kick in on quiet)
 
 cat /proc/acpi/thermal_zone/THRM/trip_points
 
 Crit (S5) : 102 C
 
 Passive 87 C : tc1 = 0 tc2 = 4 tsp = 4 devices = oxd6766bc
 
Now I have no iea what the trip points things mean, is it saying that the fans will only change speed once the temperature reaches 87 C?  And that the machine will shut down once the temperature hits 102 C.

Anyway, what do I need to to change the trip points so fans cut out at cooler temperatures and enabling frequency scaling.  ALl the guides I have found are rather confusing.

The machine is a Lenovo 300 c200, cELORON m 1.6 GHz, 512 Ram.
Thanks in advance

Michael.

---

### Post by Fred_C on 2007-01-27
Hi, I have quick question for you unrelated to the fan. I've also got the Lenovo 3000 c200.. exact same model (a bargain, no?) but I haven't been able to get the internal wireless working. Everyone seems to indicate that this card works for the get go, but I haven't had any luck. 

When I go to the Network Settings the card shows up as eth1, I configure it to my wireless router, but then no connection. In the connection properties it doesn't show up. Any advice?

Also, if you ever get the sound working please let us know!

---

### Post by zanjabeel5 on 2007-03-18
@Fred


I had the c200 too, 
I'm very new to ubuntu (one week)
for the wireless I did
sudo apt-get update
sudo apt-get install network-manager-gnome

then the wireless worked perfectly (with WPA)
but still no luck with the sound : (
YOU GURU's ... HELP US

as for the fan I  just think ubuntu runs way more cooler and quiter on the c200 than XP.

---

