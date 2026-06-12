---
title: "[SOLVED] Automatic Updates not working"
date: 2008-07-11
forum: General Help
---

### Post by Shne on 2008-07-11
I have had this problem for quite some time now but I didn't notice exactly when it started.
My problem is basically that Ubuntu doesn't automatically check for updates.
I have to open the update manager manually and hit "Check" myself to see if there are any updates and since I don't remember to do this everyday, I'm missing out on important security updates for several days before I check it myself.

Software Sources looks like this:
[img]http://img79.imageshack.us/img79/4147/screenshotsoftwaresourcgw7.png[/img]

When I have checked for updates manually and it has found updates, the "updates found" icon appears in the notification area like it should.
sudo apt-get update/upgrade/check gives no errors.

---

### Post by dcstar on 2008-07-12
> **Shne said:**
> I have had this problem for quite some time now but I didn't notice exactly when it started.
My problem is basically that Ubuntu doesn't automatically check for updates.
......

/etc/cron.daily/apt should exist, and you should have the **anacron** package installed along with the **update-notifier** package.

---

### Post by Shne on 2008-07-12
> **dcstar said:**
> /etc/cron.daily/apt should exist, and you should have the **anacron** package installed along with the **update-notifier** package.

/etc/cron.daily/apt does exist and I have the packages anacron and update-notifier installed.

Edit: and still it doesn't check automaticly.

---

### Post by Shne on 2008-07-18
I'm still having this problem.
A thought has crossed my mind: could it be because I'm use Hibernate instead of just shutting down every night?

---

### Post by Shne on 2008-08-22
It appears to have fixed itself.

---

