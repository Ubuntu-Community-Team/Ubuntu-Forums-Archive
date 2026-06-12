---
title: "smtp.comcast.net cert failure"
date: 2008-10-26
forum: General Help
---

### Post by joel@parke.ods.org on 2008-10-26
Hi all,

Apparently, two days ago, smtp.comcast.net started failed in forwarding my email.  The message in the mail.log file is as follows:
Oct 25 12:29:31 parke postfix/qmgr[7852]: 4995ABEC08E: from=<jan@parke.ods.org>, size=47328, nrcpt=2 (queue active)
Oct 25 12:29:31 parke postfix/smtp[13943]: certificate verification failed for smtp.comcast.net[76.96.62.117]:587: untrusted issuer /C=US/O=VeriSign, $
Oct 25 12:29:32 parke postfix/smtp[13943]: 4995ABEC08E: to=<mwatson@boston.k12.ma.us>, relay=smtp.comcast.net[76.96.62.117]:587, delay=1.3, delays=0.0$
Oct 25 12:29:32 parke postfix/smtp[13943]: 4995ABEC08E: to=<megwats@gmail.com>, relay=smtp.comcast.net[76.96.62.117]:587, delay=1.3, delays=0.05/0.18/$
Oct 25 12:29:32 parke postfix/qmgr[7852]: 4995ABEC08E: removed

I have run update-ca-certificates, but that didn't help.  Apparently our email have been down for a few days.  NOT GOOD.  I am certain that someone out there knows what is causing this and how to fix it.  Any help would be greatly appreciated!

Thanks,
Joel Parke

---

### Post by cariboo on 2008-10-26
What does Comcast say about the problem, it could be something on their end that is misconfigured.

Jim

---

### Post by joel@parke.ods.org on 2008-10-26
Hi Jim,

I contacted Comcast and they replied:
That is not a comcast issue, Joel.  It is an issue on your server.   It could be time and date or security.   

Anyone else have an idea?

Thanks much,
Joel

---

### Post by joel@parke.ods.org on 2008-10-26
I just switched over to gmail and I have the same problem:
Oct 26 14:25:18 parke postfix/smtp[9215]: certificate verification failed for smtp.gmail.com[209.85.201.109]:587: untrusted issuer /C=ZA/ST=Western Ca$
O

So the question is, which certificate is failing and how can I determine why?

Thanks much,
Joel

---

### Post by agathian on 2008-10-26
Well - i am not a postfix expert.. just general observation..

From the error messages you have posted, it looks like comcast is furnishing a certificate from Verisign and your postfix doesnt recognize Verisign as a trusted issuer.

Same case with gmail for Western CA. 

You might want to search in postfix manual/forums as to how to get it to trust Verisign, etc.. It would be just installing the root CA or something

---

### Post by kc5hhq on 2009-01-12
You need to append the verisign certs to your postfix install. You can download them from [https://www.verisign.com/support/roots.html](https://www.verisign.com/support/roots.html) . Look at [http://www.mailinglistarchive.com/postfix-users@postfix.org/msg00967.html](http://www.mailinglistarchive.com/postfix-users@postfix.org/msg00967.html) for reference.

---

