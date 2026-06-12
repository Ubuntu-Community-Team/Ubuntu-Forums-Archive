---
title: "smartctl strange behavior"
date: 2011-07-22
forum: Hardware
---

### Post by lo.j on 2011-07-22
hi all.

on some of my disks, not everyone, i experienced this behavior.

i run smartctl and it says the classical```
$ smartctl -t short /dev/sde

smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Jul 22 11:18:27 2011

Use smartctl -X to abort test.
```

the strage thing is that if i then run```
$ smartctl -l selftest /dev/sde

smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12478         -
# 2  Short offline       Completed without error       00%     12478         -
# 3  Short offline       Completed without error       00%     12461         -
# 4  Short offline       Completed without error       00%     12461         -
# 5  Short offline       Completed without error       00%     12458         -
# 6  Short offline       Completed without error       00%     12434         -

```
it lists all of my previous tests but the current one in progress is not shown... it seems that it has not been started at all.

does anyone know why?
thanks...

---

### Post by lo.j on 2011-07-22
ok, i got it.

it is possible to keep an eye on the progress percentage with:```
smart -c /dev/sde
```

i found out that, in the other way, the current process is not always being listed... and i don't understand why...

thanks anyway.

---

