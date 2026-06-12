---
title: "Fix for day zeroing out on ACPI Wakeup timestamps on some mobos in 7.10 yet?"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by mattp52 on 2008-03-20
Had this working perfectly in Feisty but recently upgraded. The issue is that setting the wakeup time and checking it before shutdown looks good but the system does not wake-up. After a manual start, checking the ACPI wakeup timestamp shows the day value has been zeroed out.

I'm using an ASUS K9N-Neo motherboard.

```

$ uname -r
2.6.22-14-generic
$ sudo sh -c 'echo "+2008-00-00 00:03:00" > /proc/acpi/alarm'
$ cat /proc/acpi/alarm
2008-03-20 18:17:57

```

Manual restart...
```

$ cat /proc/acpi/alarm
2008-03-00 18:17:57

```

I've tried all the fixes I could find including the one logged at the end of [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139846")  bug page.

Does anyone know if this is this resolved in a later kernel release?

---

### Post by Fisslefink on 2008-04-06
Still broken in current gutsy and hardy heron beta.  I just reverted back to Feisty :-/  Definitely make a backup (I recommend Partimage) before upgrading.

My Mobo:  Asus P4P800E-Deluxe

-- Fisslefink

---

