---
title: "Processor works a lot when Ubuntu is started"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by commodore on 2006-03-13
Every day when I start Ubuntu I hear how the processor goes wild. I always start out with browsing the web. What can cause it? Is there some updating or something?

---

### Post by Stormbringer on 2006-03-13
A few minutes after system-boot some cron-jobs (scheduled maintainance tasks) will be executed --- including a check for available updates.

Depending on the speed of your machine this may take 2-5 minutes - and while it's running you may see a higher load on the CPU and maybe also hear some "noises" from your hard drive while it's doing some I/O.

Cheers,
Storm.

---

