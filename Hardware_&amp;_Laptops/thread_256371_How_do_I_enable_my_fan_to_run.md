---
title: "How do I enable my fan to run???"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by jipzzz on 2006-09-12
I have an acer Travelmate 4001 WLCi with newly installed dapper 6.06.1

My processor is a Pentium M (centrino) 1.5 GHz

When I had windows xp, acer had a tool that allowed me to enable my fan to run all the time.

Now my fan does not run and I do not want my laptop to overheat!!!!!!

How can I edit the ACPI (???) and get my fan to run all the time again?

Help is much appreciated!

-Jeff

P.S. 109 F and climbing

---

### Post by jipzzz on 2006-09-13
bump

Can I reset the trip points to activate the fan at cooler conditions?

Reason I want to do this is I have only one fan and when it runs it keeps the hard drive cool too.  I just replaced my original hard drive maybe because of heat.

---

### Post by Mize on 2006-09-13
Can you set fan trip points in your BIOS? I would assume this would work with any OS so long as no app overrides it.

---

### Post by jipzzz on 2006-09-13
Still trying to fix this with more issues:

~$ echo 20 > /proc/acpi/thermal_zone/THRM/polling_frequency

bash: /proc/acpi/thermal_zone/THRM/polling_frequency: Permission denied

~$ sudo echo 20 > /proc/acpi/thermal_zone/THRM/polling_frequency

bash: /proc/acpi/thermal_zone/THRM/polling_frequency: Permission denied

same happens with echo "90:90:80:45:38" > trip_points

How can I gain priviledge to fix this?????


results of cat /proc/acpi/thermal_zone/THRM/trip_points

critical (S5):           100 C
passive:                 92 C: tc1=2 tc2=3 tsp=100 devices=0xc14565a0
active[0]:               68 C: devices=0xdeec4a40
active[1]:               61 C: devices=0xdeec4bc0

These temps are not low enough for my judgement

---

### Post by jipzzz on 2006-09-14
bump

---

### Post by compuguy1088 on 2006-09-30
> **jipzzz said:**
> bump

From what I've seen, try doing sudo -s and then executing the command, this seems to do the trick. Hope this works...

---

