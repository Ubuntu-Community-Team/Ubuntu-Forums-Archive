---
title: "UPS with autoshutdown feature"
date: 2010-04-06
forum: Hardware
---

### Post by deostroll on 2010-04-06
Hi,

I am looking for a brand of UPS which has an autoshutdown feature. By 'autoshutdown' I mean that I don't need to switch off the UPS manually after my system has shutdown. I am specifically hoping that the UPS driver software must have the capability of working with the ubuntu os as well. I use karmic koala as of now.

---

### Post by tgalati4 on 2010-04-06
Look for older, metal-case APC UPS.  Check craigslist for used ones, then put in fresh batteries.

Avoid the plastic case ones.  They catch fire.

apcupsd will perform autoshutdown.  You can configure it with various timers and battery-life-remaining parameters.  For example, it can shut down the machine at 30% battery-remaining, then shut down the UPS (to prevent damage when the power comes back) after another 5 minutes.  Then it will send emails or sms about power loss and shutdown.  It's not as pretty as the windows software, but it works reliably.

The smartups series can also dump data to a server that you can monitor remotely.

I've attached a couple of screenshots to show the monitoring.  The utility company has been replacing power poles, so I've experienced several outages in the past few weeks.

---

