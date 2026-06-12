---
title: "useradd -p not working?"
date: 2008-11-12
forum: General Help
---

### Post by unobserved on 2008-11-12
I'm trying to get the useradd command to work but it doesn't seem to accept -p

My command is:

```
sudo useradd -d /home/FTP/testaccount -p upload testaccount
```

The problem is, when I try to FTP in with the account, the password is not recognized. To get it working I have to:

```
sudo passwd testaccount
```

And then enter my password twice. While this isn't really a huge hassle, I'm trying to put together a utility script that will add users for me and it would be easier (and cleaner) if I didn't have to call passwd after each one and the useradd just worked as described in the manpages.

I have other FTP accounts that are setup and working, so I know it's not a problem with the FTP or the login in general, it just seems that regardless of what I try, I can not set a password for a new user unless I run passwd or change it through the GUI.

Any suggestions would help

---

### Post by jlpeifer on 2008-11-30
Yeh... I've noticed this too.  I've tried a few variants on this command including ...
> 
sudo useradd -d /home/testuser -m testuser -p testpass
- and -
sudo useradd -d /home/testuser -m testuser -ptestpass
- and -
sudo useradd -d /home/testuser -m testuser -p "testpass"


None of these seems to work. I suspect there's a guru out there who can provide an answer (nudge, nudge, hint, hint).

---

