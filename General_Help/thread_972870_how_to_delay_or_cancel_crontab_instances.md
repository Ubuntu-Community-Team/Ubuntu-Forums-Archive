---
title: "how to delay or cancel crontab instances ?"
date: 2008-11-06
forum: General Help
---

### Post by kanenas.net on 2008-11-06
I use crontab to schedule a job that runs every minute.
But, sometimes this job requires more than one minute to finish.

The question is...
I have an instance of a procedure that runs every minute through crontab.
How can i delay or cancel a new instance of the same procedure from running while the previous instance is still running?

Is it possible writing shell script, or something in php?
Is there a tutorial ?
Or is there a command ?

Thanks

---

### Post by geirha on 2008-11-06
You want to search for locking. A search for "bash locking" on google gave this as one result: [http://bash-hackers.org/wiki/doku.php?id=howto:mutex](http://bash-hackers.org/wiki/doku.php?id=howto:mutex) . Haven't read it, but looks like a solution for your problem at first glance.

---

