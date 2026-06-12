---
title: "[postfix+mysql] How to customize postfix."
date: 2008-07-30
forum: General Help
---

### Post by sanocli on 2008-07-30
Hello guys,

I just complete the installation of postfix with the mysql support. Great!!!

Now I want to customize postfix. More precisely, I have a database wich contains a lists of addresses mail blocked or granted for each of my user.

What I want to do is when postfix receives an email, check in my database if the address in the field To is present if it's the case, if the from address is :
- granted, send the email
- blocked, destroy the mail and add some information in my database
- not in the database, put the mail in the HOLD directory and put some informations in my database.

In fact it's a sort of anti-spam.

I'm a complete newbie in postfix so can someone please help. I have read a lot of how to or documentations but I still understand not much to postfix.

Thank you and have a good day.

---

### Post by sanocli on 2008-07-30
I was wondering if my solution could be to put something into smtpd_recipient_access to test if my addresses are in my database.
Am I right or not at all?

Thanks for answering my question

---

### Post by sanocli on 2008-07-31
Hello guys it's me again.

I have a question about the smtpd_recipient_access, is this feature only available for mail from internet or is this available also for the local posted mail?

Second question what do I have to do to change the behaviour of the cleanup daemon? In fact, I would like the daemon to check/put something in my database and to act in consequence.

Thanks for helping me.

Have a good day.

---

