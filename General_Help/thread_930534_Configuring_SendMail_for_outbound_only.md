---
title: "Configuring SendMail for outbound only"
date: 2008-09-26
forum: General Help
---

### Post by Rob_Quads on 2008-09-26
I have a Ubuntu 7.10 server running which has a number of RAID arrays on it. I want to set it up so that it emails me if there is a problem. AFAIK mdadm will use sendmail to send the mail to me but I have been unable to get sendmail to work.

I don't want the server to handle ANY incoming mail
For outbound I will need to connect to my smtp server to relay the message which also requires authentication 

I have looked into sendmail.cf but not found a configuration to work.

Any ideas?

---

### Post by fjgaude on 2008-09-27
You might get replies to your post if you move it over to the Server Platforms forum... more folks there know about sending mail.

---

### Post by dcstar on 2008-09-28
> **Rob_Quads said:**
> I have a Ubuntu 7.10 server running which has a number of RAID arrays on it. I want to set it up so that it emails me if there is a problem. AFAIK mdadm will use sendmail to send the mail to me but I have been unable to get sendmail to work.

I don't want the server to handle ANY incoming mail
For outbound I will need to connect to my smtp server to relay the message which also requires authentication 

I have looked into sendmail.cf but not found a configuration to work.

Any ideas?

Firstly, installing **postfix** is probably a better option, then set the appropriate config file setting to only accept connections from 127.0.0.1 (the localhost).

---

