---
title: "Join WIndows Workgroup"
date: 2008-08-19
forum: General Help
---

### Post by ProgenitorVirus on 2008-08-19
I've done this before, now can't remember if my life depended on it.  I remember it being hard to find how to the first time, but doing it was pretty straightforward.

Anyways, I want to be able to make my Ubuntu machine, join a Windows Workgroup.

net join MYWGROUP returned the error:

cannot join as standalone machine

So I'm lost.  Any help?

Thanks!

---

### Post by Titan8990 on 2008-08-19
You first have to install SAMBA:

sudo apt-get install samba

Then in your smb.conf file there is a line like this:

workgroup = HOME


Just change it the workgroup you need it and restart SAMBA.

---

### Post by jimv on 2008-08-19
There's also a GUI app that will do this.  It's called Likewise-Open.

You can get it in the repos.

---

### Post by ProgenitorVirus on 2008-08-19
I used likewise-open and got an error

Unable to resolve DC name

Under Domain I put the Wokrgroup name, and I entered my computer name, then clicked join domain, it said "Administrator" so I entered my account password, and gave me the error.  Any ideas?

---

### Post by tangibleorange on 2008-08-19
```
gksu gedit /etc/samba/smb.conf
```
as suggested above, in the line that says workgroup = WORKGROUP, change WORKGROUP to your workgroup. in my file, it's at line 27, but it may be different for you.
then save the file, and run:
```
sudo /etc/init.d/samba restart
```

and you should be done.

---

### Post by jimv on 2008-08-19
I think you need to use the fqdn.

---

### Post by s4l on 2010-10-03
Ok I had the same issue and fixed it by removing the '#' sign for:
Security = domain

The default setting of the smb.conf file sets it as 

# Security = blahblah

change it to:

Security = domain
I didn't have to restart samba for it to work right i.e. it went from giving me a  'cannot join as standalone machine' message to requesting a password for my domain account I used to add the server.

Thanks much for the help people!
Woot!
:guitar:

---

