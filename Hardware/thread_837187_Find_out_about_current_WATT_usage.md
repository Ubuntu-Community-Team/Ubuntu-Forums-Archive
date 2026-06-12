---
title: "Find out about current WATT usage?"
date: 2008-06-22
forum: Hardware
---

### Post by jo.angel on 2008-06-22
How can I find out the current WATT usage of my notebook?
I am not talking about the WATT usage in battery mode, but when plugged into a regular 220V plug. 

[COLOR="Red"] cat /proc/acpi/ac_adapter/ACAD/state[/COLOR]

just shows me Í am online, but whoz my watt usage?

---

### Post by sdennie on 2008-06-22
I don't think it is possible.  I believe that when you see watt usage using a tool like powertop, it's an inferred value based on how quickly the battery is being drained.  If there is no battery to drain, I'm not sure it's possible to figure out how much power the system is using (which is why powertop doesn't display the information when not on battery).

---

