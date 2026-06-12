---
title: "Any way to query the AC adapter info?"
date: 2012-03-06
forum: Hardware
---

### Post by wujj123456 on 2012-03-06
Hi
 
I am looking for a way to identify my AC adapter  info.   I have two adapters, one is 65W and the other is 90W.   From  /proc/acpi/ac_adapter/AC/state, I can only check if power adapter is  connected, but I want to extract the detailed power adapter  information.  Something similar to /proc/acpi/battery/BAT0/info. 
 
In  addition, I want to write some bash script that behave differently  depending on if power is plugged in.  Is there a way to get informed  after user plug in/pull the power cord?  I can continuously cat  /proc/acpi/ac_adapter/AC/state, but I want a more elegant solution such  as catching the event or signal.  
 
Thanks.

---

