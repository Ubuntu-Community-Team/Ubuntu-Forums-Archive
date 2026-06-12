---
title: "Download Scheduler?"
date: 2008-09-22
forum: General Help
---

### Post by RVcook on 2008-09-22
I've just upgraded to Hardy Heron and so far so good.  Wireless works, printer works, and finally got Java installed.

My question: Does anyone know of a utility that I can install which will allow me to schedule my downloads (NOT just Ubuntu upgrades)?  I have a FAP limit so if I can download between 2 and 5 am, regardless of how large the download is, it does not apply toward my 30 day FAP.

I know there are such animals for Windoze, but I haven't found one for Linux.  Am I missing something obvious?

I hope someone can help me out.  Thank you!

RVcook

---

### Post by Taxman415a on 2008-09-22
It looks like d4x will do that, but I've never used it. sudo aptitude install d4x 
will install it. Also you can of course use wget and set up a cron job to do your downloading. That's sort of the canonical Linux/Unix command line way to do it.
Looks like the gnome-schedule package can do task scheduling in general as well as a gui interface to cron.
Here's the [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) if you want that.

---

### Post by RVcook on 2008-09-22
> **Taxman415a said:**
> It looks like d4x will do that, but I've never used it. sudo aptitude install d4x 
will install it. Also you can of course use wget and set up a cron job to do your downloading. That's sort of the canonical Linux/Unix command line way to do it.
Looks like the gnome-schedule package can do task scheduling in general as well as a gui interface to cron.
Here's the [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) if you want that.

Thank you for your reply.  I will definitely check those out!

Thanks again.

RVcook

---

