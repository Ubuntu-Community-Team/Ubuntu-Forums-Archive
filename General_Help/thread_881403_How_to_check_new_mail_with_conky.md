---
title: "How to check new mail with conky?"
date: 2008-08-06
forum: General Help
---

### Post by tensecor on 2008-08-06
Hi,I just install the conky.And the Folloing is my conyrc file.
I am using the fetchmail to get mails from the mail server.The new mail will be delivered to my mialbox ~/Mail/inbox.
So,according to the conky documents.I use the following code to check new mails.
```
${color}      You have ${color3}${new_mails  /home/tensecor/Mail/inbox  60s}${color}  new mail(s) 
```
There,60s means to check the new mail by the interval of 60 sec.
But,there seems to be a problem.
[COLOR="DarkRed"]It would not refresh the new_mails count untill I restart the conky application.[/COLOR]
Dose anyone konows how to check new mails with conky cyclically.

---

### Post by fluxer on 2008-10-31
> **tensecor said:**
> Hi,I just install the conky.And the Folloing is my conyrc file.
I am using the fetchmail to get mails from the mail server.The new mail will be delivered to my mialbox ~/Mail/inbox.
So,according to the conky documents.I use the following code to check new mails.
```
${color}      You have ${color3}${new_mails  /home/tensecor/Mail/inbox  60s}${color}  new mail(s) 
```
There,60s means to check the new mail by the interval of 60 sec.
But,there seems to be a problem.
[COLOR="DarkRed"]It would not refresh the new_mails count untill I restart the conky application.[/COLOR]
Dose anyone konows how to check new mails with conky cyclically.

I'll try to find a solution for the mail problem (because I want that too), but could you tell me where you got the special fonts?

Thanks

---

