---
title: "ddrescue resumes but log file resets"
date: 2021-02-13
forum: Hardware
---

### Post by potatochip on 2021-02-13
Hello, I've been trying to recover a dodgy HDD using ddrescue.

I have used it with a logfile so it should resume but I've noticed that the log file resets when I restarted the process even though the img size did not.
The onscreen info while it's running also indicates that it has started from fresh.

My question is whether it will use the existing img data and skip over any bits it already has recovered and so be faster than the estimate it currently displays.

I would have thought the onscreen display would show the cumulative effects if it had resumed so 50% first run plus 2% second run = 52% instead of just 2%.

Perhaps related is that the firt run was interupted by the dodgy drive going offline and when Ubuntu detected it again it had switched from /dev/sda to /dev/sdb. The command specifies the same img and log/map file so I don't think this sould be an issue.

Does anyone have the knowledge they can share on this?

---

