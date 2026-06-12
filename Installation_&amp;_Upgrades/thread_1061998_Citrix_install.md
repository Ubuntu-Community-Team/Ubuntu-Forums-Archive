---
title: "Citrix install"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by tuxusa on 2009-02-06
I am using Ubuntu 8.10 and need to remote into my company’s network. I am able to install Citrix without error but I get a security error when I try to logon.

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Error:
You have not chosen to trust “DigiCert Global CA”, the issuer of the server’s security certificate (SSL error 61).

Thanks in advance.

---

### Post by dstew on 2009-02-06
I don't know a lot about certificates, but there is a command line program called [certmgr]("http://pwet.fr/man/linux/commandes/certmgr") that can look at the state of your certificates. Maybe you could get a clue from that. Enter ```
sudo certmgr -list Trust
```and see what you get. There also seem to be ways to get and SSL certificate too.

---

