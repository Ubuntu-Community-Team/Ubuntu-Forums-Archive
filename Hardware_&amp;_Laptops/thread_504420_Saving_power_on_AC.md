---
title: "Saving power on AC"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2007-07-19
Dear Ubuntuers,

I have been questing to reduce my laptops power usage and to lower its CPU temps.  I noticed today that when it is left to idle when running on battery, the CPU temp is ~5 degrees lower than on AC.  So I want to use  whatever state it runs on when on battery, on AC too.  I assume it's going to be an ACPI event I need to trigger manually--but which?

Thanks!

Simon

edit:  I've tried executing the script /etc/acpi/events/battery but to no avail.  I can't find *any* info on this. 

The messages I get from /var/log/acpid when I remove and the reconnect the ac are:

root@frege:/var/log# tail -f acpid
[Thu Jul 19 22:28:24 2007] notifying client 5506[0:0]
[Thu Jul 19 22:28:24 2007] completed event "processor CPU2 00000081 00000000"
[Thu Jul 19 22:28:24 2007] received event "battery BAT0 00000080 00000001"
[Thu Jul 19 22:28:24 2007] notifying client 5131[0:0]
[Thu Jul 19 22:28:24 2007] notifying client 5506[0:0]
[Thu Jul 19 22:28:24 2007] executing action "/etc/acpi/power.sh"
[Thu Jul 19 22:28:24 2007] BEGIN HANDLER MESSAGES
[Thu Jul 19 22:28:24 2007] END HANDLER MESSAGES
[Thu Jul 19 22:28:24 2007] action exited with status 0
[Thu Jul 19 22:28:24 2007] completed event "battery BAT0 00000080 00000001"
[Thu Jul 19 22:29:29 2007] received event "ac_adapter AC0 00000080 00000001"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] executing action "/etc/acpi/power.sh"
[Thu Jul 19 22:29:29 2007] BEGIN HANDLER MESSAGES
[Thu Jul 19 22:29:29 2007] END HANDLER MESSAGES
[Thu Jul 19 22:29:29 2007] action exited with status 0
[Thu Jul 19 22:29:29 2007] completed event "ac_adapter AC0 00000080 00000001"
[Thu Jul 19 22:29:29 2007] received event "hotkey ATKD 00000058 00000000"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] completed event "hotkey ATKD 00000058 00000000"
[Thu Jul 19 22:29:29 2007] received event "processor CPU1 00000080 00000000"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] completed event "processor CPU1 00000080 00000000"
[Thu Jul 19 22:29:29 2007] received event "processor CPU1 00000081 00000000"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] completed event "processor CPU1 00000081 00000000"
[Thu Jul 19 22:29:29 2007] received event "processor CPU2 00000080 00000000"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] completed event "processor CPU2 00000080 00000000"
[Thu Jul 19 22:29:29 2007] received event "processor CPU2 00000081 00000000"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] completed event "processor CPU2 00000081 00000000"
[Thu Jul 19 22:29:29 2007] received event "battery BAT0 00000080 00000001"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] executing action "/etc/acpi/power.sh"
[Thu Jul 19 22:29:29 2007] BEGIN HANDLER MESSAGES
[Thu Jul 19 22:29:29 2007] END HANDLER MESSAGES
[Thu Jul 19 22:29:29 2007] action exited with status 0
[Thu Jul 19 22:29:29 2007] completed event "battery BAT0 00000080 00000001"
[Thu Jul 19 22:29:29 2007] received event "battery BAT0 00000081 00000001"
[Thu Jul 19 22:29:29 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:29 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:29 2007] executing action "/etc/acpi/power.sh"
[Thu Jul 19 22:29:30 2007] BEGIN HANDLER MESSAGES
[Thu Jul 19 22:29:30 2007] END HANDLER MESSAGES
[Thu Jul 19 22:29:30 2007] action exited with status 0
[Thu Jul 19 22:29:30 2007] completed event "battery BAT0 00000081 00000001"
[Thu Jul 19 22:29:30 2007] received event "ac_adapter AC0 00000080 00000001"
[Thu Jul 19 22:29:30 2007] notifying client 5131[0:0]
[Thu Jul 19 22:29:30 2007] notifying client 5506[0:0]
[Thu Jul 19 22:29:30 2007] executing action "/etc/acpi/power.sh"
[Thu Jul 19 22:29:30 2007] BEGIN HANDLER MESSAGES
[Thu Jul 19 22:29:30 2007] END HANDLER MESSAGES
[Thu Jul 19 22:29:30 2007] action exited with status 0
[Thu Jul 19 22:29:30 2007] completed event "ac_adapter AC0 00000080 00000001"

---

### Post by anubhavrocks on 2007-07-19
You can use the 
"cpufreq-set" and "cpufreq-info" utilities to effectively control the cpu frequencies and governors.

---

### Post by simoncullen on 2007-07-19
Thanks.  The effect on the temperature is not, so far as I can tell, due to CPU frequency scaling.  It will run cooler on battery when set to ondemand, than it will on ac set to powersave!


> **anubhavrocks said:**
> You can use the 
"cpufreq-set" and "cpufreq-info" utilities to effectively control the cpu frequencies and governors.

---

### Post by simoncullen on 2007-07-20
I found today that Gnome seems to have a "low power mode" -- does anyone know if this could be responsible for the temperature drop?

Cheers,
Simon

---

