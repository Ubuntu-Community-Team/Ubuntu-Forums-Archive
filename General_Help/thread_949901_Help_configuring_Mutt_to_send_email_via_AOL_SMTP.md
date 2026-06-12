---
title: "Help configuring Mutt to send email via AOL SMTP?"
date: 2008-10-16
forum: General Help
---

### Post by martynp on 2008-10-16
Hi All,

Decided to give Mutt a try and had no problem setting it up to read my AOL account and show my emails.

However, I just cannot get it to send. AOL uses Port 587 for smtp and I have read as much as I can about SMTP in Mutt.

I have tried it's inbuilt SMTP command in my .muttrc with no joy and also tried sSMTP with no joy either.

Has anyone got Mutt sending email via the AOL smtp servers and if so can you point me in the right direction to make it work.

Many Thanks

---

### Post by andrew.46 on 2008-11-25
Hi,

Regarding ssmtp did you use something like this in /etc/ssmtp/ssmtp.conf:

```
mailhub=smtp.aol.com:587
```

I am not sure of the name of the aol smtp server though.

 Andrew

---

### Post by martynp on 2008-11-25
Hi,

Thanks for the reply. I have been away for a few weeks but I DID get ssmtp working for AOL but NOT from withing mutt.

In the end I decided to stay with Thunderbird for the time being.

Many Thanks,

Martyn

---

