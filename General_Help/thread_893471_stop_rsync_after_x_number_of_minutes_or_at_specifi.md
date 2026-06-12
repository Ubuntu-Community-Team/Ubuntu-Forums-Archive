---
title: "stop rsync after x number of minutes or at specified time"
date: 2008-08-18
forum: General Help
---

### Post by SteveGodfrey on 2008-08-18
I'm using rsync to backup my system to an off-site location. The upload speed of my internet connection is very low so the backup is sometimes still running the following morning. I have a time slot when my ISP doesn't perform any traffic shaping so I want to use this window to perform the backup (22:00 to 13:00).

Can anyone suggest how I can get rsync to stop at a specified time or after x number of minutes/hours?

I keep stumbling across a rsync patch called time-limit but can't see how to apply the patch.

Thanks

---

### Post by HalPomeranz on 2008-08-18
One approach would be to simply have an external process that kills all rsync jobs at 13:00.  You could do this via cron with an entry like:

0 13 * * * /usr/bin/pkill rsync

For more information on cron, see [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

