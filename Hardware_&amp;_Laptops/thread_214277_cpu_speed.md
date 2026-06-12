---
title: "cpu speed"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Zarin on 2006-07-12
I recently installed Dapper on my HP nc6000 laptop with a 1600MHz pentium M.
After bootup the cpu speed is only 600MHZ. With Breezy on the same laptop, the cpu speed was 1600MHZ with the powercord plugged in an 600MHz when unplugged. Now it is 600 whether it is plugged in or not. I have tried to disable automatic speedsteep in BOIS but that does not help.
I can set the cpu speed with cpufreq-set but after a reboot it is back to 600 MHZ.
I would like to have it as it was with Breezy, full speed with power and throttled on battery but I have no idea what could be wrong.

---

### Post by mrcl on 2006-07-12
Hi Zarin
It seems you are using powernow deamon for saving energy, you don need to work at 1600MHz all the time.
Try to make a test, run some program that requires cpu power, e.g compile a program form source, and take a look in th cpu frenquncy, if powernowd is working weel, it will increase at the operation.

---

### Post by Zarin on 2006-07-12
Seems to be powernowd.Thanks for the help.

---

