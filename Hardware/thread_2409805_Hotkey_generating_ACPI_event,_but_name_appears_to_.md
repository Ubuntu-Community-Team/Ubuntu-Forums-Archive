---
title: "Hotkey generating ACPI event, but name appears to be GUID"
date: 2019-01-07
forum: Hardware
---

### Post by kenneth-fechter on 2019-01-07
I am attempting to debug an issue with an ACPI hotkey not working on a laptop. 

using the following commands all yield the same results. ```
acpi_listen
``` ```
netcat -U /var/run/acpid.socket
``` ```
acpid -d -l 
```

the event appears to be part of a GUID, in my case 56322276-8493-4C[]

the [] in this case is a diamond with a question mark in it, which I believe to be a unicode character.


Searching the partial GUID returns the ideapad-laptop module, however I believe the event is not matching the existing GUID fully, and thus causing the hotkey not to fire any events through the handler. How do I get the full GUID of the event?

---

