---
title: "How do I schedule Unison with cron?"
date: 2008-07-24
forum: General Help
---

### Post by 47_MasoN_47 on 2008-07-24
Alright, I've never used cron before and frankly I have no idea how to.  I've read a few things but it makes no sense at all to me.

I have Unison setup to sync my files to a USB drive and it works fine if I run it by hand.  I want to schedule it to run every night at 7pm but as I said earlier, I have no idea how to.

If someone could tell me exactly what to do, that would be awesome!

Thanks!

---

### Post by northern lights on 2008-07-24
Create a textfile in your /home folder and name it "cronjobs.txt".

Open it and add the line ```
0 19 * * * /usr/bin/unison [options]
```

Then run ```
crontab -u USERNAME cronjobs.txt
```

where USERNAME is your username. Verify with ```
crontab -l
```

The syntax of a cronjob is

*minutes(0-59) hours(0-23) day(0-27/28/29/30) month(0-11) weekday(0-6) command*

where a * stands for "any value"

---

### Post by 47_MasoN_47 on 2008-07-24
Thank you very much.  That simple post was a thousand times easier than all these pages and pages of tutorials.  Concise is the way to go, I thank you kind sir.

---

### Post by northern lights on 2008-07-24
Not to worry. Notice the slight changes (edited the above while you posted the reply).

--> just installed unison to verify few things...

---

### Post by Krydahl on 2008-07-24
A slight expansion on:

> 0 19 * * * /usr/bin/unison [options]

When you did your manual run of unison you will have created a profile. To run in background from cron, use:

```
unison -batch "profilename"
```

The quotes are needed.

Also, if you find you're still struggling with cron, there is a gui tool to make it easier to set up called gnome-schedule.

---

### Post by salkeld17 on 2009-06-10
Thanks so much for this. Gnome-schedule and Unison plus your command took me less than 1 minute to setup! Awesome.

---

### Post by ducksun43 on 2009-06-11
hello, [http://sunoano.name/ws/public_xhtml/time.html](http://sunoano.name/ws/public_xhtml/time.html) and [http://sunoano.name/ws/public_xhtml/unison.html](http://sunoano.name/ws/public_xhtml/unison.html) helped me a lot. mabye you like em too :)

---

