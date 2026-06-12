---
title: "samba question"
date: 2005-12-04
forum: General Help
---

### Post by Coogan on 2005-12-04
Is there any way to set up Samba so that authentication can be bypassed by IP or MAC address?  In other words, if I try to connect from my primary desktop system (using XP), I don't want to get prompted for a username or password.  However, if I try to connect to it from any other system on my network, I get prompted for a username and password.

---

### Post by Ocxic on 2005-12-04
I'm pretty sure you can't just bypass it, tho you could just setup everything so that you don't need a username and password, that way you could just hit enter/next or whatever and not need to type anything in. other then that i dunno.

---

### Post by daedalusman on 2005-12-04
How do you set it up so that it doesn't require a password? I have been trying to figure that one out but haven't been able to yet.

---

### Post by Ocxic on 2005-12-04
when setting up network shares, don't set a username/password for it.
then when the dialog come up just click connect/next/etc...

---

### Post by tonysathre on 2005-12-04
i dont think that would work, u cant connect until u do smbpasswd and smbpasswd -a <username> to set up a samba account, i dont think what your trying to do is poosbile unless u specify a null password, but u would still need a username because it has to be a local account and i dont think u can have a null username

---

### Post by chipmonk010 on 2005-12-04
If you use the following config you dont need to enter any password, you will be logged in as user 'nobody' so any files you create will be owned by 'nobody'


[global]
workgroup = workgroup
netbios name = server
security = share
browseable = yes
hosts allow = 192.168.1.

[shared]
path=/shared
read only = no
guest ok = yes


hope this helps
cheers
chris

---

