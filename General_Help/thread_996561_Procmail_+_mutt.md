---
title: "Procmail + mutt"
date: 2008-11-28
forum: General Help
---

### Post by lesjohn on 2008-11-28
I'm trying to get email from gmail with fetchmail and deliver to a mailbox using procmail.  It works, but when I read it with mutt, it shows up as one very long message that includes all the headers and bodies of all the messages.  I note there's no "From " at the top of messages -- not sure if this is the problem.  Thanks for any suggestions!

My .fetchmailrc:
poll imap.gmail.com with proto imap
     user 'address@gmail.com' there with password 'pass' is 'johnl' here     
     options ssl keep
     mda "procmail .procmail/gmail"

.procmail/gmail is:
MAILDIR=$HOME/.mail
DEFAULT=$MAILDIR/gmail

---

### Post by andrew.46 on 2008-12-01
Hi,

I have not seen this syntax before:

```
mda "procmail .procmail/gmail"
```

Is there a special reason for this? You could try syntax similar to that seen here:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

and see if things run a little better.

  Andrew

---

