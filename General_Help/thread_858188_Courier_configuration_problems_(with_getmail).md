---
title: "Courier configuration problems (with getmail)"
date: 2008-07-13
forum: General Help
---

### Post by gurkburk on 2008-07-13
Im trying to configure Courier+getmail on my server (8.04), but im having some problems.
Ive installed courier-mta,courier-imap, and getmail.

Now, in my "getmailrc" file I have configured it to deliver to Maildir, I want each users's mails to end up in /home/user/maildir and then have the courier-imap read from there.
My getmailrc:
> cat /etc/getmail/testdummy.rc
[retriever]
type = SimpleIMAPRetriever
server = mail.mydomain.com
username = myaccountname
password = ********

[destination]
type = Maildir
path = ~testdummy/Maildir/

If trying manually:
> /usr/bin/getmail
getmail version 4.7.7
Copyright (C) 1998-2007 Charles Cazabon.  Licensed under the GNU GPL version 2.
SimpleIMAPRetriever:mytestaccount@mydomain.com:143:
  msg 1/5 (4140 bytes) delivered
  msg 2/5 (3954 bytes) delivered
  msg 3/5 (3974 bytes) delivered
  msg 4/5 (3977 bytes) delivered
  msg 5/5 (1269 bytes) delivered
  5 messages (17314 bytes) retrieved, 0 skipped
Note: I have sent 5 mail's to that adress to have something to actually download and read.

When connecting with a client (using outlook express for testing), it does connect properly, but it doesnt get any mails.
Since getmail is recieving 5 mails everytime I try, I get the feeling it should be courier that needs fixing.

Sidenot: I tried renaming /home/testdummy/Maildir and then getmail wont function, it complains of a directory problems, so obviously it should be courier thats the problem (?).

Sidenote2: I didnt just mkdir Maildir... I did a "maildirmake Maildir" in /home/testdummy/ then chown to testdummy:testdummy a chmod to get getmail to function.

Sidenote3: in /etc/courier/imapd I have MAILDIRPATH=Maildir and also in /etc/default/courier MAILDIR="Maildir"

Any tips and hints?
Help appreciated :)

---

