---
title: "permissions"
date: 2008-09-20
forum: General Help
---

### Post by gishaust on 2008-09-20
Hi everyone,
 
I trying and gftp into the server I know that it is a permission issue by I don't know how to fix it. ssh and gftp works as I use it all the time with another user.

I have created a new user so that i  can ssh into the box.

sudo useradd abby -p password -d /home/ftp/abby -s /bin/false
(i know about the shell it is a protective measure).

My issue is if I try ls -l I get the following
drwxr-xr-x 2 root root      4096 2008-09-20 16:44 abby

So I sudo chown abby abby and get the following
drwxr-xr-x 2 abby root      4096 2008-09-20 16:44 abby

I still can't get the gftp to talk to the server it says permission denied
what am I doing wrong?

---

