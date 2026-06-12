---
title: "Random power offs (ACPI problem)"
date: 2012-01-08
forum: Hardware
---

### Post by Procrat on 2012-01-08
Hi everyone!
Last night my laptop powered off without a warning. After I rebooted, it happened a second time after about an hour or so.
Everything was running smoothly and then in a sudden moment, it just powered off.

I'm not much of an expert, but I took a look at syslog and the following log entries are written just before the crash. They are the same in both cases.

```
Jan  7 23:53:34 stijn-W150HRM kernel: [ 3390.982185] ACPI: EC: input buffer is not empty, aborting transaction
Jan  7 23:53:34 stijn-W150HRM kernel: [ 3390.982201] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110413/evregion-478)
Jan  7 23:53:34 stijn-W150HRM kernel: [ 3390.982222] ACPI Error: Method parse/execution failed [\_TZ_.TZ0_._TMP] (Node ffff88023305d078), AE_TIME (20110413/psparse-536)
Jan  7 23:53:35 stijn-W150HRM kernel: [ 3391.490037] ACPI: EC: input buffer is not empty, aborting transaction
Jan  7 23:53:35 stijn-W150HRM kernel: [ 3391.989858] ACPI: EC: input buffer is not empty, aborting transaction
Jan  7 23:53:36 stijn-W150HRM kernel: [ 3392.489704] ACPI: EC: input buffer is not empty, aborting transaction
Jan  7 23:53:36 stijn-W150HRM kernel: [ 3392.489720] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20110413/evregion-478)
Jan  7 23:53:36 stijn-W150HRM kernel: [ 3392.489744] ACPI Error: Method parse/execution failed [\_TZ_.TZ0_._TMP] (Node ffff88023305d078), AE_TIME (20110413/psparse-536)
Jan  7 23:53:36 stijn-W150HRM kernel: [ 3392.997544] ACPI: EC: input buffer is not empty, aborting transaction
Jan  7 23:53:37 stijn-W150HRM kernel: [ 3393.497382] ACPI: EC: input buffer is not empty, aborting transaction
```

---

### Post by Procrat on 2012-01-10
By the way, I'm not using Maverick anymore like my profile shows at the moment, but Oneiric.
Also:
```
$ **uname -a**
Linux stijn-W150HRM 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Procrat on 2012-02-02
I hate to self-bump this thread, but this problem still occurs about 4 times a week.
Any (yes, ANY!) ideas are welkom; :)

---

### Post by whiskers751 on 2012-05-01
These problems crop up too much!
Fix for now:
Hold shift at boot
Select an OLDER kernel (lower numbers)
(maybe look in Prev Linux Versions)
Hit Enter

THIS IS NOT PERMANENT....

---

### Post by Procrat on 2012-05-01
Thanks for the reply!
I don't however have any previous kernel versions installed. Is there a version known to not have such problems? I believe every 3.x version caused this.

But I don't think my laptop has crashed in the last month, so maybe there's been an update regarding this? I switched to 12.04, so I'm using Linux 3.2.0 at the moment.

---

### Post by whiskers751 on 2012-05-02
I think the old 2.6 kernels are great for relic laptops :)
You might have to compile it yourself if it isn't in the repos.
Good old 'make'.

---

### Post by Procrat on 2012-05-03
Thanks!
My notebook isn't much of a relic however. Soms specifications:> Intel HM65 Express Chipset
Intel Core i7-2630QM
NVidia GT555 with Optimus
Battery: 11.1 Volt - 5600mA - 62.16WhIt's not assembled by a major notebook producer though.

---

