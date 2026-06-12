---
title: "What does the 's' mode bit mean?"
date: 2008-10-11
forum: General Help
---

### Post by shaggy999 on 2008-10-11
Hi. I used rsync today to mirror the cygwin packages from a server and I had run it once as a normal user and then as sudo and then as a normal user which complained because it couldn't write to some of the files. So did some chown and chmod stuff mainly:

chown -R root:root cygwin/
chmod -R u=rwX,g=rwX,o=rX cygwin/

and some interesting stuff occurred. On some, but not all of the directories I got a "directory not found error" and permissions retained as "rwxrwsr_x" for those directories. This is the first time I've come across an s bit. So I checked the man page and it says:

"Set user or group ID on execution"

which is a great way of informing the user without informing the user. I have no idea what that description means.

---

### Post by Sam on 2008-10-11
Read this: [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

---

