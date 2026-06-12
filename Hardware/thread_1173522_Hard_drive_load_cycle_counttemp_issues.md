---
title: "Hard drive load cycle count/temp issues??"
date: 2009-05-29
forum: Hardware
---

### Post by tpoirots on 2009-05-29
So, I was reading through the thread posted by "nicedude" on this issue, and it got me concerned. Does anyone know if this is still a valid issue to be concerned about, with the latest ubuntu?
I ran the command:
date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
which produced the following output:
Fri May 29 20:19:03 EDT 2009
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       2719
194 Temperature_Celsius     0x0002   157   157   000    Old_age   Always       -       35 (Lifetime Min/Max 16/37)
Should I be concerned? I have rerun the command 2-3 times over the pasy hour, with no change in results...
Notebook is:
Lenovo T60P
Harddisk: Hitachi: HTS721010G9SA00
Thanks and regards,
T. Poirot

---

