---
title: "smart (smartctl) test on hard drive immediately finishes without doing anything."
date: 2018-09-08
forum: Hardware
---

### Post by david503 on 2018-09-08
I run:

[COLOR=#000000]smartctl -t long /dev/sdb[/COLOR]

[COLOR=#000000][/COLOR]And I've done that on other workstations before and normally the (second, hence "sdb") drive immediately starts crunching and the drive light blinks. Nope.

[COLOR=#000000]And while it's running, (or not)
[/COLOR]
[COLOR=#000000]smartctl -a /dev/sda[/COLOR]

I get:

Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        51         -


I mean I get that instantly.  So it didn't actually do anything right?  

Thanks,

d

---

### Post by TheFu on 2018-09-09
When I ask for a test, smartctl tells me to wait X minutes before requesting the results.  I think it is usually 4 min for short tests and a few hours for long tests.  I don't recall, since I run long tests through cron every week and the results are always waiting.  The manpage for smartctl probably has more details.  There are offline and online tests. What those mean is complicated.

---

