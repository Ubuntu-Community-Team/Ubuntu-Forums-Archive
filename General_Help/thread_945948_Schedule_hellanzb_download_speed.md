---
title: "Schedule hellanzb download speed"
date: 2008-10-12
forum: General Help
---

### Post by sab0tage on 2008-10-12
I'm looking for a way to schedule the download speed of hellanzb deamon. It dawned on me that maybe I could do this via a cron job.

For example, during the day, I don't want to tie up my connection, but in the evening i'd like to have full speed.

Anyone doing something like this or have a better method?

---

### Post by deoneR on 2009-07-21
hello,

sorry for pulling out this old thread, but i would really like this feature too!
anyone got an idea how to get a speed scheduler for hellanzb?

---

### Post by mister_p_1998 on 2009-07-21
You can only schedule stop & start with cron, I have Hellanzb & Ktorrent start at midnight & run until I come home from work, they are then killed at 18:00.
Steve

---

### Post by Andcor on 2009-12-27
You might be able to do this by changing the speed directive in hellanzb.conf and then stopping and starting the daemon. However, it seems that hella isn't that good at actually obaying the speed directive in the conf file.

---

