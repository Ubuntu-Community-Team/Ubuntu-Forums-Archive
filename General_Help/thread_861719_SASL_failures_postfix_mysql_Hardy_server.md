---
title: "SASL failures postfix mysql Hardy server"
date: 2008-07-16
forum: General Help
---

### Post by dragonator on 2008-07-16
I've been searching in vain for a solution to a failure using SASL and SMTP_AUTH on a Hardy server install.  All the howto references tell you how, but despite 3+ weeks of searching all the docs and howtos I can find, the only thing in common seems to be the repeated reports of it not working on Hardy even though it worked fine before.  Even some reports of existing working setups being broken by the upgrade from 7.10 to 8.04.

Does anyone have any pointers to bug reports, etc., that may indicate that the devs are either aware of the problem or have determined an appropriate workaround?  BTW, I don't consider removing postfix from it's chroot as a viable workaround, which happens to be the only possible solution I've found so far.  I did try it with no luck just to validate the rest of my installation, but I can't say I'd put the server into production in that mode even if it worked.

For anyone interested I'm attempting to setup postfix with SMTP_AUTH using SASL, Courier for IMAP and POP support, all running virtual domains.  I'm using mysql for account storage, and postfixadmin to administer the whole thing, atmail, rcube, and squirrelmail for webmail access.  It's roughly based on this howto:

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04")

---

### Post by crudolphy on 2008-07-27
I have the same problem.  Hardy 8.04 server, following the same how to:

Anyone have any answers?
```
Jul 27 17:34:16 crud-04 postfix/master[7576]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jul 27 17:35:16 crud-04 postfix/smtpd[7614]: warning: SASL per-process initialization failed: generic failure
Jul 27 17:35:16 crud-04 postfix/smtpd[7614]: fatal: SASL per-process initialization failed
Jul 27 17:35:17 crud-04 postfix/master[7576]: warning: process /usr/lib/postfix/smtpd pid 7614 exit status 1
Jul 27 17:35:17 crud-04 postfix/master[7576]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

---

