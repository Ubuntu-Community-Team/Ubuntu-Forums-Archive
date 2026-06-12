---
title: "supplemental vs supplementary vs [regular] groups"
date: 2008-07-20
forum: General Help
---

### Post by redchair on 2008-07-20
Can somebody please explain to me the difference between supplemental groups and regular groups. The goal here is not really to get my scanner to work, but was discovered in the process.

I have successfully done a
$ sudo usermod -a -G scanner [username]
which added [username] to the line in /etc/group for scanner. The membership in /etc/group is static and is not affected by a restart.

However when I use the command
$ groups
I get:
[username] othergroup1 othergroup2... but no scanner group

$ man usermod
The above command provides the man page for usermod which explains how I was able to use that command to add myself to "scanner" as a supplemental group.

How can I get a list of supplemental group membership because "groups" does not seem to list supplemental groups. What is the advantage of using supplemental groups? Is the correct term "supplemental" or "supplementary" as mentioned in the usermod man page?

EDIT: I used "groups" once before I restarted, but did not use groups again after I restarted. I guess group membership is refreshed on restart.

---

