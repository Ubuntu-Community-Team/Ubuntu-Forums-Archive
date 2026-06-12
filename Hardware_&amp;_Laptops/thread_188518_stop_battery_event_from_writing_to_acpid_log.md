---
title: "stop battery event from writing to acpid log"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by usergentoo on 2006-06-04
Every so many seconds the acpid log is written to showing this 
```
[Sun Jun  4 06:41:16 2006] received event "battery BAT1 00000080 00000001"
[Sun Jun  4 06:41:16 2006] notifying client 4103[108:108]
[Sun Jun  4 06:41:16 2006] executing action "/etc/acpi/power.sh"
[Sun Jun  4 06:41:16 2006] BEGIN HANDLER MESSAGES
[Sun Jun  4 06:41:16 2006] END HANDLER MESSAGES
[Sun Jun  4 06:41:16 2006] action exited with status 0
[Sun Jun  4 06:41:16 2006] completed event "battery BAT1 00000080 00000001"
[Sun Jun  4 06:41:16 2006] received event "battery BAT2 00000080 00000000"
[Sun Jun  4 06:41:16 2006] notifying client 4103[108:108]
[Sun Jun  4 06:41:16 2006] executing action "/etc/acpi/power.sh"
[Sun Jun  4 06:41:16 2006] BEGIN HANDLER MESSAGES
[Sun Jun  4 06:41:16 2006] END HANDLER MESSAGES
[Sun Jun  4 06:41:16 2006] action exited with status 0
[Sun Jun  4 06:41:16 2006] completed event "battery BAT2 00000080 00000000"
[Sun Jun  4 06:42:21 2006] received event "battery BAT2 00000080 00000000"
[Sun Jun  4 06:42:21 2006] notifying client 4103[108:108]
[Sun Jun  4 06:42:21 2006] executing action "/etc/acpi/power.sh"
[Sun Jun  4 06:42:21 2006] BEGIN HANDLER MESSAGES
[Sun Jun  4 06:42:21 2006] END HANDLER MESSAGES
[Sun Jun  4 06:42:21 2006] action exited with status 0
[Sun Jun  4 06:42:21 2006] completed event "battery BAT2 00000080 00000000"
[Sun Jun  4 06:42:21 2006] received event "battery BAT1 00000080 00000001"
[Sun Jun  4 06:42:21 2006] notifying client 4103[108:108]
[Sun Jun  4 06:42:21 2006] executing action "/etc/acpi/power.sh"
[Sun Jun  4 06:42:21 2006] BEGIN HANDLER MESSAGES
[Sun Jun  4 06:42:21 2006] END HANDLER MESSAGES
[Sun Jun  4 06:42:21 2006] action exited with status 0
[Sun Jun  4 06:42:21 2006] completed event "battery BAT1 00000080 00000001"

```

Im guessing its monitoring the battery or something. How would I make this stop.

---

### Post by Arthur Archnix on 2008-05-19
I'm on Hardy right now, and I've read on launchpad that you add "-l /dev/null" to the command line.

I think they meant you do "sudo acpid -l /dev/null" and the manpage for acpid supports this assumption. But it just results in an error, saying: > acpid: can't open /proc/acpi/event: Device or resource busy

I'm not sure if its the correct command. And i'm not sure why it's not working. I would also like to disable acpid logging though, so if anyone can help... please do.

---

### Post by Arthur Archnix on 2008-05-26
I've pasted the solution for how to disable acpid logging [here]("http://ubuntuforums.org/showpost.php?p=5045679&postcount=7").

---

