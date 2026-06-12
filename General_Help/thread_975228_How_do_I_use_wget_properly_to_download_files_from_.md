---
title: "How do I use wget properly to download files from sourceforge.net?"
date: 2008-11-08
forum: General Help
---

### Post by kevdog on 2008-11-08
I'm trying to write a script to automate a download process from sourceforge.net.  The problem is that the actual file link has a bunch of redirects that wget is unable to follow.

Here is my example:

wget [http://sourceforge.net/tracker/download.php?group_id=92888&atid=676821&file_id=274176&aid=1940289](http://sourceforge.net/tracker/download.php?group_id=92888&atid=676821&file_id=274176&aid=1940289)

That is not exactly working -- unless I download it manually using firefox.

How can I get wget to navigate and eventually download the .tar.gz file?

---

### Post by kevdog on 2008-11-08
Just in case anyone wants to know you need the use of quotes and to designate a download file name for clarity:

wget "http://sourceforge.net/tracker/download.php?group_id=92888&atid=676821&file_id=274176&aid=1940289" -O Ubuntu_Human.tar.gz

---

### Post by superkikim on 2011-09-20
Thank you :-) 

Was a long time ago, but you saved my day ;-)

---

### Post by oldos2er on 2011-09-20
Closed, necromancing.

---

