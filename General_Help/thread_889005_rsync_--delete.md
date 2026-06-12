---
title: "rsync --delete"
date: 2008-08-13
forum: General Help
---

### Post by boblemur on 2008-08-13
hey all, im trying to sync with 3 computers.

1 server
1 desktop
1 laptop

i know that --delete will remove files iv deleted from the original when i sync. but i was wondering if...

i get the latest version of files on my laptop... write a textfile.TXT, and then sync my changes back...

then if i am on my desktop and i make a 2nd textfile2.TXT and sync my changes... will this delete textfile.txt because the desktop does not have this file??

sorry if thats a little confusing, and thanks for any help in advance

---

### Post by fsmithred on 2008-08-16
Yes, because rsync can't tell the difference between a file that was deleted and a file that never existed. It's either there to be copied, or it isn't, and if you use the --delete option, then anything that isn't there on the source computer won't be there on the destination computer when you get done.

---

