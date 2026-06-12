---
title: "What hdparm setting do you use and recommend?"
date: 2018-09-24
forum: Hardware
---

### Post by webmiester on 2018-09-24
hi everyone,

We can use hdparm to tell the harddisk when to sleep.  I just found out that mine has an APM = 0ff.

My server runs an application and database on it, and the company runs for 24 hours, but the querries it will be getting isnt necessarily continuous.  In fact in the early hours of the morning, on sundays, and on holidays, we will find several hours when there will be no querries made.  The files are just all text data, no heavy music or pictures being exchanged.

I read that overly aggressive HD power management will lead to a shorter life for the HD due to frequent parking and power spiking.

With so many hdparm settings to choose from, what setting do you use and what do you think you can recommend for me.  Thanks

---

### Post by TheFu on 2018-09-24
I don't buy "green" HDDs for anything other than backup storage, never for primary storage.

I prevent disks from stopping.  I also tweak the read-ahead buffers to improve performance. Every disk is different, so local testing is needed.

The original site is gone, but the Way-Back Machine has a copy still:
[https://web.archive.org/web/20120622060730/http://www.robthomson.me.uk:80/2011/03/30/tuning-kvm-guests-you-need-to-do-it/](https://web.archive.org/web/20120622060730/http://www.robthomson.me.uk:80/2011/03/30/tuning-kvm-guests-you-need-to-do-it/)

---

### Post by webmiester on 2018-09-25
> **TheFu said:**
> I don't buy "green" HDDs for anything other than backup storage, never for primary storage.

I prevent disks from stopping.  I also tweak the read-ahead buffers to improve performance. Every disk is different, so local testing is needed.

The original site is gone, but the Way-Back Machine has a copy still:
[https://web.archive.org/web/20120622060730/http://www.robthomson.me.uk:80/2011/03/30/tuning-kvm-guests-you-need-to-do-it/](https://web.archive.org/web/20120622060730/http://www.robthomson.me.uk:80/2011/03/30/tuning-kvm-guests-you-need-to-do-it/)

Why do you prevent disks from stopping?  Wont it be better if they go to sleep when they arent being used?

---

