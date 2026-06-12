---
title: "why log files fill so fast"
date: 2008-08-17
forum: General Help
---

### Post by flintflake on 2008-08-17
Ok.. this is a continuation of a the solved "out of space thread".   I've had to do delete the log files twice in like 3 months because they got to be several gigs and I ran out of space.


Why does it fill so fast?   how can i stop it from growing so fast?   Can I clear those files on logoff?

---

### Post by flintflake on 2008-08-17
anyone?

---

### Post by ModelM on 2008-08-17
In the file:

/etc/logrotate.conf

you can set how often the logfiles are rotated (weekly, daily, etc) and also how many weeks of old logs to store.

I don't know if this will solve your problem, but it might be a start.

---

### Post by keithweddell on 2008-08-17
I don't know why your logs are filling up but have a look at logrotate.  Reduce the rotation period. Reduce the number of stored copies.  Save some space.

Edit - Beat me to it.

---

