---
title: "acpi lid issue with repeating events"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by exobuzz on 2005-09-08
Hi,

I have a problem with my laptop (travelmate 8104wlmi). When I close the lid, acpid gets repeated lid button events and so it runs the screenblank/lock screen over and over again. I'm just wondering if this could be a DSDT problem or a problem related to the way acpid detects the lid button event ?

[Tue Sep  6 03:19:41 2005] received event "button/lid LID 00000080 0000017b"
[Tue Sep  6 03:19:41 2005] executing action "/etc/acpi/lid.sh"
[Tue Sep  6 03:19:41 2005] BEGIN HANDLER MESSAGES
[Tue Sep  6 03:19:41 2005] END HANDLER MESSAGES
[Tue Sep  6 03:19:41 2005] action exited with status 1
[Tue Sep  6 03:19:41 2005] completed event "button/lid LID 00000080 0000017b"
[Tue Sep  6 03:19:41 2005] received event "button/lid LID 00000080 0000017c"
[Tue Sep  6 03:19:41 2005] executing action "/etc/acpi/lid.sh"
[Tue Sep  6 03:19:41 2005] BEGIN HANDLER MESSAGES
[Tue Sep  6 03:19:41 2005] END HANDLER MESSAGES
[Tue Sep  6 03:19:41 2005] action exited with status 1
[Tue Sep  6 03:19:41 2005] completed event "button/lid LID 00000080 0000017c"
[Tue Sep  6 03:19:41 2005] received event "button/lid LID 00000080 0000017d"
[Tue Sep  6 03:19:41 2005] executing action "/etc/acpi/lid.sh"
[Tue Sep  6 03:19:41 2005] BEGIN HANDLER MESSAGES
[Tue Sep  6 03:19:42 2005] END HANDLER MESSAGES
[Tue Sep  6 03:19:42 2005] action exited with status 1
[Tue Sep  6 03:19:42 2005] completed event "button/lid LID 00000080 0000017d"
[Tue Sep  6 03:19:42 2005] received event "button/lid LID 00000080 0000017e"
[Tue Sep  6 03:19:42 2005] executing action "/etc/acpi/lid.sh"
[Tue Sep  6 03:19:42 2005] BEGIN HANDLER MESSAGES
[Tue Sep  6 03:19:42 2005] END HANDLER MESSAGES

---

### Post by exobuzz on 2005-09-08
There is definately something odd going on with acpi on my laptop with the lid button pressed in it does indeed get continuous acpi events.

root@travelmate:/proc/acpi# cat event
button/lid LID 00000080 00000065
button/lid LID 00000080 00000066
button/lid LID 00000080 00000067
button/lid LID 00000080 00000068
button/lid LID 00000080 00000069
button/lid LID 00000080 0000006a
button/lid LID 00000080 0000006b
button/lid LID 00000080 0000006c
button/lid LID 00000080 0000006d
button/lid LID 00000080 0000006e
button/lid LID 00000080 0000006f
button/lid LID 00000080 00000070
button/lid LID 00000080 00000071
button/lid LID 00000080 00000072
button/lid LID 00000080 00000073
button/lid LID 00000080 00000074
button/lid LID 00000080 00000075
button/lid LID 00000080 00000076
button/lid LID 00000080 00000077
button/lid LID 00000080 00000078
button/lid LID 00000080 00000079
button/lid LID 00000080 0000007a
button/lid LID 00000080 0000007b

hmmmm

---

