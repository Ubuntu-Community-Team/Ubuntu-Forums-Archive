---
title: "General Sending Mail Help Needed"
date: 2008-10-01
forum: General Help
---

### Post by nomaam on 2008-10-01
Hello:

I am new to the mail server world and am having some problems sending mail from my server running Ubuntu.

I have tried using Sendmail, Exim and PostFix to send email through php with the same results. Syslog shows the following for every attempt to send outgoing email to other various email providers:

---------
computername postfix/smtp[8848]: 1889C17A029C: to=<testemail@gmail.com>, relay=none, delay=4361, delays=4211/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[xx.xx.xxx.xx]:25: Connection timed out)
---------

I have read that if I want to send email from my server I must have a reverse domain name or 'PTR' in order to pass the email filters. How would I do this? 

I have several domain names registered all being linked to my single server which has virtual hosts separating them. 

If someone could provide some tips it would be much appreciated. 

Thanks

Nomaam

---

### Post by nomaam on 2008-10-02
.

---

### Post by cariboo on 2008-10-03
Have a look at this howto:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

It should help.

Jim

---

