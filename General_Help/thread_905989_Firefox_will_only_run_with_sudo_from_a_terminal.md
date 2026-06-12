---
title: "Firefox will only run with sudo from a terminal"
date: 2008-08-30
forum: General Help
---

### Post by SnowPunk98 on 2008-08-30
Not sure what happened, it will only run from a terminal right now if I do it with sudo. I have renamed the .mozilla folder, reinstalled, and done a purge uninstall and reinstall.

If I do just firefox from a terminal I get the below as an output and firefox won't start

```
(firefox:5713): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by quibbler on 2008-08-31
Check the Permissions of the folder .mozilla, and if it is root, change it to user.

Regards quibbler

---

### Post by vfeinman on 2008-10-01
I was having the same issue / problem. I didn't know how to fix it either, but I tried quibbler's suggestion. That didn't seem to do it. However, I noticed I tried to do it in root. So I closed terminal, reopened. Now I saw "uname@<whatever>:~$"

from here I executed: 
sudo chown -R uname ~/.mozilla

typed in the password when prompted. Then I typed in 
ls -al | grep .mozilla

to confirm my uname owned the directory. 

The third column is your uname. should look like...
"drwx------  4 uname root   4096 2008-09-30 19:46 .mozilla"

After doing the above steps, mozilla started for me!

---

