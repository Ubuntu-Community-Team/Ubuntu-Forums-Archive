---
title: "Help: Connection dropped by IMAP server No such file or directory"
date: 2008-11-28
forum: General Help
---

### Post by datek on 2008-11-28
Hi all,

I'm new to ubuntu, i've just installed ubuntu server and configured a mail server using the following instructions [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

The problem is that i can't login into squirrelmail...i get this error:

"ERROR: Connection dropped by IMAP server."

looking to the mail.log file i see this:

"imapd-ssl: chdir Maildir: No such file or directory"


I type this: "telnet localhost 143" and i get:

"* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready."

then i type this:

"a login [email]email@mydomain.com[/email] password"

and i get this:

"* BYE [ALERT] Fatal error: Maildir: No such file or directory
connection closed by foreign host."

please help!!!

Thanks in advice!

---

### Post by hyper_ch on 2008-11-28
I always follow the perfect howtos on [http://www.howtoforge.com](http://www.howtoforge.com) and thsoe perfect howtos by falco just work fine.

---

