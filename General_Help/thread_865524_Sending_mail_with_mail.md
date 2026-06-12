---
title: "Sending mail with mail"
date: 2008-07-20
forum: General Help
---

### Post by pieroxy on 2008-07-20
Hi there,

I upgraded from Edgy a couple of weeks back, and now my "mail" command doesn't send mails anymore....

I am used to use it with:
```
echo Blah  | mail -s "Synchronization RAID `date`" dummytest@gmail.com
```

This used to work, and I remember having to configure an SMTP server back there, but I can't remember where...

Now I get:

```
echo Blah  | mail -sv "Synchronization RAID `date`" bummytest@gmail.com
Can't send mail: sendmail process failed with error code 1

```

Any idea ?
Thanks

---

### Post by cariboo on 2008-07-20
You need to have an MTA like **exim4** or **postfix** to send mail from the command line. Both are available in the repositories.

Jim

---

### Post by pieroxy on 2008-07-21
Thanks for the tip.

I do have exim4 installed... I had it installed also on Edgy...

How do I test it to send an email ? I tried this, with no error message, but I never received an email...

```
$ exim4 -bs
220 pieroxy-edgy ESMTP Exim 4.69 Mon, 21 Jul 2008 07:16:16 +0200
HELO dude
250 pieroxy-edgy Hello pieroxy at dude
MAIL FROM:pieroxy@blahblah
250 OK
RCPT TO: dummyadress@gmail.com
250 Accepted
DATA
354 Enter message, ending with "." on a line by itself
Subject: Coucoucoucoucoucoucou
Ca roule ?
.
250 OK id=1KKnmU-0005m1-7z
QUIT
221 pieroxy-edgy closing connection
$
```
Thanks for any help.

---

### Post by d.celestine on 2008-07-23
Can someone provide step-by-step procedures to configure postfix. What I am trying to do is. I need my HTML form to send an email using postfix and sendmail which is used by PHP. I am not sure which direction I should going!!!

---

### Post by brian_p on 2008-07-23
> **pieroxy said:**
> Thanks for the tip.

I do have exim4 installed... I had it installed also on Edgy...

How do I test it to send an email ? I tried this, with no error message, but I never received an email...


Have a look in /var/spool/exim4/ to see if it left the system.

---

### Post by pieroxy on 2008-07-28
In /var/spool/exim4/ I have three directories, two of whch are empty (input and msglog). The db directory contains:

```
/var/spool/exim4/db# ls -al
total 32
drwxr-x--- 2 Debian-exim Debian-exim  4096 2008-07-05 23:01 .
drwxr-x--- 5 Debian-exim Debian-exim  4096 2007-05-07 16:43 ..
-rw-r----- 1 Debian-exim Debian-exim 12288 2008-07-25 07:35 retry
-rw-r----- 1 Debian-exim Debian-exim     0 2007-05-07 16:45 retry.lockfile
-rw-r----- 1 Debian-exim Debian-exim 12288 2008-07-25 07:35 wait-remote_smtp_smarthost
-rw-r----- 1 Debian-exim Debian-exim     0 2007-12-17 16:20 wait-remote_smtp_smarthost.lockfile

```

Does that help ?
Thanks

---

### Post by brian_p on 2008-07-29
> **pieroxy said:**
> 

Does that help ?
Thanks

/var/spool/exim4/input being empty means there is nothing awaiting sending. You should find a record of sent mail in 
/var/log/exim4/.

---

