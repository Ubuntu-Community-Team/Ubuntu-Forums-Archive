---
title: "NTP - open port"
date: 2008-07-20
forum: General Help
---

### Post by change_mode on 2008-07-20
Just wondering, why does updating the system clock via NTP support need an open port? Is there an option for it to only update on system start and then close the port?
The weather information for example doesn't need this.

---

### Post by brian_p on 2008-07-20
> **change_mode said:**
> Just wondering, why does updating the system clock via NTP support need an open port? Is there an option for it to only update on system start and then close the port?
The weather information for example doesn't need this.

There is constant bidirectional traffic between your server and other servers so that the time on your machine is correct. I suppose you could set up a cron job to stop your server after some set time has elapsed. Or you could remove ntp and use chrony instead.

---

