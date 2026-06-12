---
title: "How to enable authentication on a shared printer."
date: 2018-01-04
forum: Hardware
---

### Post by joep11 on 2018-01-04
I have a Xerox WorkCentre 6515DN printer, which is connected to my Ubuntu home server. I also have a LDAP running on this Ubuntu home server with some users in it. 

Now I would like to let my Ubuntu home server share this printer within my LAN for Windows, Linux and macOS devices. But only users with valid LDAP entry (user) should be allowed to print.

Can anyone help me to solve my challenge?

---

### Post by pdc on 2018-01-05
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

is there anything here to help you?

---

### Post by sccman on 2018-01-05
Xerox has an online PDF manual for your printer. Page 278 explains how to configure your printer on an LDAP server:

[http://download.support.xerox.com/pub/docs/WC6515/userdocs/any-os/en_GB/wc6515_ug_en-us.pdf](http://download.support.xerox.com/pub/docs/WC6515/userdocs/any-os/en_GB/wc6515_ug_en-us.pdf)

---

### Post by joep11 on 2018-01-08
> **pdc said:**
> [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

is there anything here to help you?

Unfortunately not.

> **sccman said:**
> Xerox has an online PDF manual for your printer. Page 278 explains how to configure your printer on an LDAP server:

[http://download.support.xerox.com/pub/docs/WC6515/userdocs/any-os/en_GB/wc6515_ug_en-us.pdf](http://download.support.xerox.com/pub/docs/WC6515/userdocs/any-os/en_GB/wc6515_ug_en-us.pdf)

It is only for the login at the printer terminal / web interface but not for IPP/SMB/JetDirect or any other protocol.


Maybe I will explain my project again:

Printer (Xerox WorkCentre 6515 DN) --LAN-- Ubuntu Server --LANs-- 100 User PCs (Mac/Win/Linux)


Situation right now:
- I have already attached my printer via LAN to my Ubuntu server.
- Ubuntu server is running a LDAP DB where every of these 100 users has an entry (user / pw).
- Printer and Client PCs are in different subnets but.
- Ubuntu Server has two IPs (for each subnet one)


What I want:
- Now I want to share this printer through Ubuntu server to the 100 clients.
- The client MUST only be allowed to print if he authenticates successfully against his entry in the LDAP DB.
- Otherwise his print job must get rejected.

Question:
- How can I configure the Ubuntu server to realize the wanted situation above?

---

### Post by sccman on 2018-01-09
Well without knowing what you're trying to do with the printer or the server, can any of the 100 users connect to your home server at all using LDAP? That would be a good start.

---

### Post by joep11 on 2018-01-11
Yes, of course. Every of the 100 users can connect to the Ubuntu home server.

---

