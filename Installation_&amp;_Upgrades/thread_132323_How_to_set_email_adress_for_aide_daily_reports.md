---
title: "How to set email adress for aide daily reports?"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by Sebastian Stein on 2006-02-18
Folks, it is driving me crazy. I already asked this in several forums, but still no answer.

I have installed the aide package. I configured it and created the necessary database. Now, daily a report is generated and send to root@`/etc/mailname`. But I want that email to be sent to admin@localhost. 'admin' is my user I'm working with.

My first attempt was to set the email address in /etc/cron.daily/aide:


```
MAILTO="${MAILTO:-admin@localhost}"
```

Afterwards I tried to also set the email address in /etc/crontab:

```
MAILTO=admin@localhost
```

Still it does not work. I'm really not sure about the problem. I have installed postfix using a "dial-up" setting to send emails through a POP3/SMTP account. Also sending an email to admin@localhost for example from within mutt works great.

Any ideas how to fix this?

Sebastian

---

### Post by Sebastian Stein on 2006-02-19
[QUOTE=Sebastian Stein]

```
MAILTO="${MAILTO:-admin@localhost}"
```
[/QUOTE]

I found it by myself. The above line in /etc/cron.daily/aide was wrong, It must be:

```
MAILTO="admin@localhost"
```

Sebastian

---

