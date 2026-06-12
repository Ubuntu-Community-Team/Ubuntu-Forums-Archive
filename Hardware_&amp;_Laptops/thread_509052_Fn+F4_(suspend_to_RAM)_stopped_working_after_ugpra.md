---
title: "Fn+F4 (suspend to RAM) stopped working after ugprade to Fiesty"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by chiron80 on 2007-07-25
Since upgrading to Fiesty (7.04), Fn+F4 (suspend to RAM) is no longer working on my Thinkpad Z60m. It was definitely working in Edgy (6.10). I'm trying to figure out what changed to stop it from working.

I used "acpi_listen" to verify that when I press the button an ACPI event is produced (ibm/hotkey HKEY 00000080 00001004). One thing I noted is that if I press it several times quickly, only one event is produced. If I wait a minute or so and press it again, it works again.

```
$ cat /etc/acpi/events/ibm-sleepbtn

# /etc/acpi/events/ibmsleepbtn
# Called when the user presses the sleep button

event=ibm/hotkey HKEY 00000080 00001004
action=/etc/acpi/sleepbtn.sh
```

```
$ cat /etc/acpi/sleepbtn.sh

#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_SLEEP
```

I added a line to sleepbtn.sh that output text to a file, and verified that sleepbtn.sh is indeed called when I press Fn+F4, so I am getting as far as acpi_fakekey $KEY_SLEEP.
I looked at /usr/share/acpi-support/key-constants, and $KEY_SLEEP=142. If I call acpi_fakekey 142 nothing happens. This is where the trail goes cold, I'm not sure where to go next, and I can't find any documentation on acpi_fakekey.

Suspend to RAM works just fine if I use gnome-power-manager (from the notification area), or if I use the "Suspend" option in the "Quit..." menu.

Any suggestions?

Thanks,
- Ben

---

