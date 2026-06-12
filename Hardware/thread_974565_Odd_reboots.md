---
title: "Odd reboots"
date: 2008-11-07
forum: Hardware
---

### Post by LeBurt on 2008-11-07
Hi all,

I'm getting unexpected reboots in Intrepid, I also had them once in a while in Hardy before.

System log doesn't appear to show anything abnormal except for ACPI warnings just prior:

```
Nov  7 16:24:19 ciabata kernel: [ 1098.772868] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Nov  7 16:30:01 ciabata /USR/SBIN/CRON[7591]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  7 16:32:11 ciabata kernel: [ 1570.775360] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - F5, should be EC [20080609]
Nov  7 16:32:11 ciabata kernel: [ 1570.776803] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - F5, should be EC [20080609]
Nov  7 16:32:11 ciabata kernel: [ 1570.778449] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - F5, should be EC [20080609]
Nov  7 16:35:40 ciabata syslogd 1.5.0#2ubuntu6: restart.
``` 

I have a hunch that this might be related to insufficient power from the PC's power supply or else a hot CPU.

How would I go about making sure of that? Anyone seen something similar?

Thanks!

---

