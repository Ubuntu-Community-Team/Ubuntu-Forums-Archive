---
title: "Is it possible to do this with cron?"
date: 2008-08-18
forum: General Help
---

### Post by SoCalChris on 2008-08-18
Would it be possible to schedule something like this in the cron file using only a single line?

Have something scheduled for 12:30am, and the same command scheduled for 1:45am?

The only way I can think of doing this would be to use

30,45 12,1 * * * mycommand

The problem with this is that it will run mycommand at 12:30, 12:45, 1:30 and 1:45 instead of just the two times that I need this. 

Is it possible to do this using just a single line?

Thanks

---

### Post by tamoneya on 2008-08-18
i dont know how that can be done with a single line.  Sorry.  What is so bad about two lines?  Also how bad would it be to run it at 12:30 and 1:30.

---

### Post by SoCalChris on 2008-08-18
I didn't think it would be possible, thanks.

The reason that it specifically needs to be on a single line is because I'm defining a recurring schedule in a database, and am trying to see if I can base the schema for that recurrence on the cron format since it is fairly simple and flexible. It looks like it won't work for what I need though (At least not without modification).

Thanks for the reply.

---

### Post by HermanAB on 2008-08-18
You could make a script that will run at the first time instance using the cron daemon and let this script schedule another script to run some time later using the At daemon.

Cheers,

Herman

---

