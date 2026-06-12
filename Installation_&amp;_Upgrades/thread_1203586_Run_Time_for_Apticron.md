---
title: "Run Time for Apticron"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by cdnjay on 2009-07-03
Hi,

I recently set up apticron to run on my server but the only problem is that it's running daily around 7:00 PM.  Is there a way I can change it to run at 6:00 AM daily?

Thanks!

Jason

---

### Post by bttw on 2011-01-07
I had the same question, and since no one answered, I'll share.

```
sudo nano /etc/cron.d/apticron
```

Edit the first two values to the time you'd like it to run.

---

