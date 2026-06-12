---
title: "[SOLVED] Bittorrent Clients that Start / Stop at a Set Time?"
date: 2008-10-23
forum: General Help
---

### Post by Vuddha on 2008-10-23
Hi all,

I'm currently using Transmission Bittorrent Client on Ubuntu 8.04. I'm happy with it, but I was wondering if anyone knows of a Bittorrent client that can be set to start at a specific time. For example, if I want to begin seeding / leeching at 2:00am, and have it stop at 10:00am, I'd like to preset to do this.

Any thoughts?

Thanks,

---

### Post by ddrichardson on 2008-10-24
You could set a cron job to execute the torrent program at a set time.

---

### Post by Vuddha on 2008-10-24
Hi,

Thanks for the reply. What's a cron job?

---

### Post by Zack McCool on 2008-10-24
ktorrent has a very effective scheduler.  Not only will it allow what you are looking for, but you could also change the maximum up/down speeds with the scheduler.

ktorrent is in the repos, but being a KDE app, it will install some of the KDE libraries to make it work.

```

sudo apt-get install ktorrent

```

I have been using it for a long time now, and it is a very nice app...

---

### Post by sdennie on 2008-10-24
As was said above, you can set a cron job to do this.  Try:

```

crontab -e

```

In the example you gave, I believe adding this to the file would work:

```

* 2 * * * DISPLAY=:0.0 transmission
* 10 * * * pkill transmission

```

I believe that will start transmission at 2am and cleanly shut it down at 10am.

---

### Post by Kinetic Being on 2008-10-24
utorrent also does this. it runs perfectly under wine, and I find that it has the best download speeds compared to any other programs I've used.

---

### Post by Vuddha on 2008-10-25
Thanks for all your help. I've installed both gnome-schedule (for the cron jobs) and ktorrent. ktorrent looks like it'll do what I need it to, but I'll explore the Task Scheduler, too.

Will mark solved. 

Thanks again.

---

