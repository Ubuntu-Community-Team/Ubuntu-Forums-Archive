---
title: "[SOLVED] Weird cron problem"
date: 2008-10-16
forum: General Help
---

### Post by tuok84 on 2008-10-16
Hi,

I made small script some time ago, which sends my (dynamic) ip address to internet, so I can make ssh connection to my home computer from work. It worked great, and I thought to put this script on my cron. I didn't manage to get it to work with cron (ssh problems), so I removed the script and uninstalled it from cron. I had fiddled with my own user's and also with root's crontab.

Now, for some odd reason, my system still tries to call this non-existent script every minute (short 1 minute interval was for testing purposes), and I have no idea why it does that. Have I missed some crucial thing here or what? Running "crontab -l" with my normal user and root user return nothing.

Can anybody help me with this? Thanks!

---

### Post by tuok84 on 2008-10-16
Never mind, I solved it (of course this happens 5 min after first post ^^), I found about system-wide crontab. My script was left there also.

---

