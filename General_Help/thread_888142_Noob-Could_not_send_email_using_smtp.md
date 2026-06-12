---
title: "Noob-Could not send email using smtp"
date: 2008-08-12
forum: General Help
---

### Post by studiogrynn on 2008-08-12
Just a heads-up.
After a dual boot install on my gateway MX6920, I was unable to send mail via either Evolution nor Thunderbird. I was unable to check the firewall status via ufw -status after logging in as su. It would not recognize that I was logged as root. Attempting to set the rule using ufw -allow 25/smtp returned "Bad Port":confused:

My quick fix was to install Firestarter, run the setup wizard and activate it. I did not need to create a specific rule set for port 25. It opened right up and mail was working right away.

It's a bit of a noob fix, but it got me up and running and will buy me a bit of time to research the ufw issue.

---

### Post by brian_p on 2008-08-12
> **studiogrynn said:**
> 

Attempting to set the rule using ufw -allow 25/smtp returned "Bad Port":confused:


Shouldn't that be either

```
ufw allow 25/tcp

```
or

```
ufw allow smtp ?
```

---

