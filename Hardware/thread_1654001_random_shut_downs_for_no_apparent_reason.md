---
title: "random shut downs for no apparent reason"
date: 2010-12-27
forum: Hardware
---

### Post by aaronp on 2010-12-27
Hi guys,

I installed a new 1GB stick of RAM beside my existing 1GB on Sunday. On Monday, twice, I came back to find my system was powered off. I figured there was issues with the RAM or it's compatibility with the other stick but ran memtest, and got no errors and also checked dmesg and lspci, and there is nothing that suggests RAM caused the power downs.
So, figuring I had CPU temperature problems I set up a cron job to log the core temps every minute so if I had another power down I could see what the temperature was right beforehand. (As I've not witnessed any of the shutdowns)

Since yesterday (Monday) it's been on all night so I figured it had resolved itself but this morning, after coming back in from outside I see it's powered down again.
My temperature log file shows the cores were both at 37 degrees at the time the log was cut and had not spiked at all any time before that, so I can't see this being an overheating problem.

Wondering if anyone has any ideas for where to look next?

thanks
Aaron

---

