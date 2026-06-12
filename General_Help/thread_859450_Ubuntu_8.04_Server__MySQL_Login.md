---
title: "Ubuntu 8.04 Server / MySQL Login"
date: 2008-07-14
forum: General Help
---

### Post by bpinkston on 2008-07-14
From a shell prompt or terminal session, I can log into the MySQL by typing:

```
mysql -u myusername -p
```

then it prompts for the password, and I login with no problem

If use the following from the shell or terminal session it is a no go. 

```
mysql -u myusername -pmypassword
```

This is a problem, because I need to cron a job to run, and it won't let the cron job log in.  It fails with the following error: 

ERROR 1045 (28000): Access denied for user 'myusername'@'localhost' (using password: YES)

Help woudl be greatly appreciated.

---

