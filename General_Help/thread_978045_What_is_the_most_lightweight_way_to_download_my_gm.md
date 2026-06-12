---
title: "What is the most lightweight way to download my gmail emails?"
date: 2008-11-10
forum: General Help
---

### Post by spibou on 2008-11-10
gmail offers you the option to use POP3 to retrieve your emails. I'm looking for an utility, as small as possible, which will download my latest emails and put them in a file. I don't want any interface for reading the emails, I only want them to go to a file. Ideally the utility should work from the command line. Is there such a thing?

---

### Post by kaptengu on 2008-11-10
Maybe fetchmail is what you are looking for. Have a look at this:
[http://mpov.timmorgan.org/2007/12/13/backup-your-gmail-account-messages-with-ubuntu-and-fetchmail/](http://mpov.timmorgan.org/2007/12/13/backup-your-gmail-account-messages-with-ubuntu-and-fetchmail/)

---

### Post by jimv on 2008-11-10
Put up an SMTP serve and have GMAIL forward to it.

Done.

---

### Post by spibou on 2008-11-11
> **kaptengu said:**
> Maybe fetchmail is what you are looking for. Have a look at this:
[http://mpov.timmorgan.org/2007/12/13/backup-your-gmail-account-messages-with-ubuntu-and-fetchmail/](http://mpov.timmorgan.org/2007/12/13/backup-your-gmail-account-messages-with-ubuntu-and-fetchmail/)
fetchmail looks promising. I had a browse at its man page and it doesn't seem as if it  offers you the possibility to put the retrieved mail in a file, you need to have a MTA running to do that but it's a start. Or perhaps it does offer you a way to put the mail in a file and I missed it.

Thank you.

---

### Post by spibou on 2008-11-11
> **jimv said:**
> Put up an SMTP serve and have GMAIL forward to it.

I don't know how to put up an SMTP server. I'm sure I could learn but it sounds like an overkill for my humble needs.

---

