---
title: "Can't get mutt to run"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2006-02-15
I set up fetchmail and procmail to put mail files in ~/mail. That works without a problem.

.procmailrc:
HOME=/home/user
DEFAULT=$HOME/mail
LOGFILE=$HOME/pmlog
----------------------------

~/mail contains some email messages of the form xxxx.msg.xxxx

So now I just want to read the emails with mutt but when I start it I get
"/home/user/mail" is not a mailbox" and I don't see any email. Here's my .muttrc

set folder = ~/mail
set spoolfile= ~/mail/
set realname = XXXX
set from = [email]user@something.com[/email]
set use_from	= yes


I've got email, so how can I get mutt to see it?

William

---

### Post by grinchy on 2006-02-15
set folder=~/
set mbox=~/mail

---

