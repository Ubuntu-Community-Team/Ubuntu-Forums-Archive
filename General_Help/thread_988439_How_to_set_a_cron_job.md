---
title: "How to set a cron job?"
date: 2008-11-20
forum: General Help
---

### Post by Dilude on 2008-11-20
Hi,

I'm looking to set up a cron job to sync my server time every 30 mins, otherwise it will go out of sync. However, i've never done this before. Would appreciate if anyone could tell me how to do it. Using Ubuntu Server 8.04

Cheers

---

### Post by DGortze380 on 2008-11-20
> **Dilude said:**
> Hi,

I'm looking to set up a cron job to sync my server time every 30 mins, otherwise it will go out of sync. However, i've never done this before. Would appreciate if anyone could tell me how to do it. Using Ubuntu Server 8.04

Cheers

Add script or command to crontab

To edit your crontab

```

crontab -e

```

To edit root's crontab, add sudo to that command

man crontab for more information

---

### Post by ilrudie on 2008-11-20
I second the above post.

Most likely you are going to want to set this up as a root cron job.

---

### Post by m_l17 on 2008-11-20
Have a look at the Wiki article:

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by bodhi.zazen on 2008-11-20
IMO, one of the most common mistakes with cron is failing to specify the full path to your applications.

Cron runs with a minimal shell, so, IMO, best to specify the full path of any command you wish to add.

---

