---
title: "Printer stuck &quot;Processing&quot; after suspend, works if reboot"
date: 2011-05-05
forum: Hardware
---

### Post by oblib on 2011-05-05
I've got a Brother HL-2040 connected to my parallel port. It works just fine until I suspend. After a suspend, it still shows up in my "lpinfo -v" until I send it a job. The job seems successful according to the CUPS logs, but it stays "Processing" until I cancel it or reboot. Once I submit a job, the parallel device no longer show up in lpinfo. If I reboot, it prints out as soon as the machine comes up.

I've tried what debug I know. I tried stopping CUPS and rmmodding lp, parport_pc, parport, and ppdev before suspending, and then restoring them all after suspending. The logs don't tell me anything useful. What else can I try?

Here's the access log for a suspended job (looks just like a good one), there are no entries in the CUPS error log.
```

localhost - - [05/May/2011:20:40:04 -0600] "POST /printers/Brother HTTP/1.1" 200 244 Create-Job successful-ok
localhost - - [05/May/2011:20:40:04 -0600] "POST /printers/Brother HTTP/1.1" 200 5499 Send-Document successful-ok

```

---

### Post by oblib on 2011-05-07
Hmm, it's still stuck.

---

