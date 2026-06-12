---
title: "old users are not recognized"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by omskates on 2009-08-30
Spent over an hour searching archives for an answer to this without result.
I have run a clean install of jaunty and did not format my /home partition.  I set up a new user at install and changed the computer name (mistake?).

In nautilus as root; all the previous user folders and files are intact & accessible as root.

The command *ls /home* does indeed list all previous users as well as the new one.  So I attempt a password change with an old user name;
*passwd 'username'*  result is *unknown user 'username'*

Please help me restore old users or user access to the old /home files

Thanks!

---

### Post by mikewhatever on 2009-08-30
Just because previous user directories are present in /home doesn't mean the users are, neither the usernames nor the passwords. All that gets overwritten during a reinstall. The only use there is after a clean install is the one you set up during the installation.

---

### Post by omskates on 2009-08-30
OK good,
Any chance at taking ownership of the previous user's folders?

---

### Post by rrplay on 2009-08-30
omskates Wrote:> In nautilus as root; all the previous user folders and files are intact & accessible as root.

> Any chance at taking ownership of the previous user's folders?

check the ownership info in the directory with ls -l

see the man pages for chown & chgrp

Example for changing ownership recursively [-R] of all files in a folder:

$ sudo chown -R {newusername] /folder-location

change the group as well 

$ sudo chgrp -R {newgroupnameifneeded} /folder-location

this should help you out.

---

### Post by omskates on 2009-08-30
Thankyou!
I used chown to adopt ownership of the entire user's home folder.  I was able to replace firefox profile easily with nautilus.  I'll be able to move any other needed folders over using nautilus.
Thanks again!

---

### Post by rrplay on 2009-08-31
Glad it worked out for you ! was not sure if you wanted all the .config files.
anyhow you can probably mark the thread as solved.

---

