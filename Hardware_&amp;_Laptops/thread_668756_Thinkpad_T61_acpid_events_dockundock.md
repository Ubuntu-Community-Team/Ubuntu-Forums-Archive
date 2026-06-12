---
title: "Thinkpad T61 acpid events dock/undock"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by juggler885 on 2008-01-15
I have a thinkpad T61 and a dock for it. It runs Ubuntu 7.10 fully updated. The problem is that I want to run a bash script when the computer docks and one when the computer undocks.

I know I have to use acpid so when the dock/undock event happens I can run the script, but I can't find the dock or undock event. I have tried acpi_listen and looked at the log file for acpid when I docked and undocked, but I don't see anything about docking (there were other events that happened, but they were about the ac adapter and cpu power usage).

I do know that ubuntu senses the dock/undock because when I type dmesg it says:
ACPI: docking
and
ACPI: undocking

How do I find acpi event for docking?

In the event folder under /etc/acpi/events I would create a file for docking called docking and it would contain:

```
#!/bin/bash
#event to run script when docking laptop

event= <what goes here?>
action=/path/to/script
```

---

