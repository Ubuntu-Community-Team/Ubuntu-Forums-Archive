---
title: "Cannot send email to external email adress using IMAP"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by ubuntogenius on 2008-03-23
I have a clean install of Ubuntu Server 7.10 with the email server option checked.
Sending and receiving seems to work fine when using Squirrelmail (webmail) for my email server.

However, when configuring an email client to use IMAP with this account, I can receive emails, but I can only send to internal mail adresses. If I send to external adresses the log says;

RCPT from unknown[<MY_IP_ADRESS>]: 554 5.7.1
Relay access denied

I don't know if the problem is the IMAP (dovecot) config or the Postfix config, or maybe it's a port problem? I assume the Ubuntu Mail server will require SSL (by default). The current ports that are open and related to this are 993, 25 and 465.

Any suggestions?

---

