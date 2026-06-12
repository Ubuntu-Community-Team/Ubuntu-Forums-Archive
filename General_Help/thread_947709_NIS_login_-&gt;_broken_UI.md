---
title: "NIS login -&gt; broken UI"
date: 2008-10-14
forum: General Help
---

### Post by strm on 2008-10-14
Hi,
I have been working on setting up some new machines in my research lab. We have an NIS server that holds all the users and passwords. I've successfully added one of the machines to the NIS server and logged in. My user interface reset to some bare minimum GNOME panels and I was able to customize it to my liking (with settings being saved to the NIS server as it also acts user home directory destination).

After repeating the procedure on a different machine using a colleague's username, he was able to login but as soon as the UI attempted to execute, a waterfall of error messages appeared including a particular one saying that the user did not have access to /tmp/gconfd-$USER`, i.e. the system was unable to create any files in the /tmp/gconfd-$USER directory upon logging in.

We have tried changing the permissions of /tmp/ to 777 (that's what it is when I login), but that didn't help. Still the system is unable to create anything in /tmp/gconfd-$USER.

One discrepancy that I did notice is for me (lets call me user1) the directory /tmp/gconfd-user1 belongs to user1 and is in group (lets call it ourgroup) ourgroup, while for my colleague (lets call him user2) the directory /tmp/gconfd-user2 belongs to user2 and is in group user2 (not ourgroup as it should be). When attempting to chgrp on that directory, the group "ourgroup" is unknown to the machine.

Any help or ideas would be greatly apprectiated.
Thanks!

---

