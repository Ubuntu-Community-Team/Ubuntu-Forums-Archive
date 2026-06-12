---
title: "Redirect Exhange E-Mail (diff server) to IMAP server (on Ubuntu system)"
date: 2008-11-26
forum: General Help
---

### Post by wesgarner on 2008-11-26
Does anyone know what software it would take to connect to the OWA exchange server and then place it in an IMAP server on the Ubuntu system to able to access from a mobile phone. (aka my phone doesn't connect to Exchange but can to IMAP)

---

### Post by Titan8990 on 2008-11-26
Exchange has built in IMAP servers. Mail does not come in or go out over OWA. OWA is basically IMAP that is hosted over HTTP.

In order to do what you are wanting to do you would have to forward all mail via SMTP to a Linux SMTP server (Exim, Postfix, etc). Then you could host that email out via an IMAP server such as Corier-IMAP.

If you did this, there would be no reason to have the Exchange server at all. My recommended options to you:


Use the Exchange IMAP server

Give your Windows server to charity and use a Linux mail server.

---

### Post by wesgarner on 2008-11-26
The problem is the OWA server is a company server that does now allow IMAP access.
I found fetchExc to fetch the OWA Exchange E-Mail and put it in an mbox-type file then Courier-IMAP to act as a new server. Would this work?

---

### Post by Titan8990 on 2008-11-26
If fetchExec works then yes. I would think that at the least the Exchange server would need to be running POP as well.

---

