---
title: "Mail"
date: 2005-11-08
forum: General Help
---

### Post by angelot on 2005-11-08
I'm a newbie, but I have some experience with debian.

After installing Breezy I installed exim4 and set it up as an "internet-site" so that it will work as an smtp-server.

Using evolution I use the localhost as smtp, but I don't know how to get local mail - i.e mail from cron, root etc.

On my debian I had an mbox in my homedir - but none in ubuntu...

Do I have to set up a pop-server to get local mail in evolution?

In evolution I can choose pop, imap, local delivery or standard unix mbox spool....

angelot
If I try pop or imap using localhost as server - no server found..
When I try local delivery og standard unix I have to specify a path - what path? I don't have any mbox....

Please help - how can I do this?

---

### Post by angelot on 2005-11-08
Found it myself...

Needed package mailutils, and now I find my local mail in /var/mail/me...

Solved!

:)

---

