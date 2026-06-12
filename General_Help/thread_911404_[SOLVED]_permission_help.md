---
title: "[SOLVED] permission help"
date: 2008-09-05
forum: General Help
---

### Post by csogilvie on 2008-09-05
Something has happened to my user account and I don't know where to look to see what's going on.

My account is the "first" account for my linux install so I do have sudo privileges.

I can't remember exactly what I did, but now, when I try to "cat" or "more" a logfile, (like the auth.log) I no longer need to sudo to view it.

If anybody could suggest what/where to look to help reset this, I'd appreciate it!

I've tried logging out and back in many times...  I also did a restart, and it still persists.

Cheers

---

### Post by yjwong on 2008-09-05
Do you need to use "sudo" for other administrative commands as well? Or is it just the log files?

On my system, I have tested that I can view auth.log without sudo as well.

Extra information: 

Permission information for mine is:
```
yjwong@yjwong:~$ ls -al /var/log/auth.log
-rw-r----- 1 syslog adm 89392 2008-09-06 03:55 /var/log/auth.log
```

Which means, auth.log is readable by users in the groups "syslog" and "adm", which I am in, as shown here:

```
yjwong@yjwong:~$ groups
yjwong adm disk uucp dialout fax cdrom floppy tape audio dip www-data video plugdev scanner admin fuse pulse-access pulse-rt sambashare vmc
```

---

### Post by csogilvie on 2008-09-05
Yes, I need to use sudo for most things... for example I can't edit auth.log without using sudo.

I have not changed anything with my account settings, but now sudo is no longer required to view the logs.

I find it strange because it changed without me doing it.

My permissions for auth.log are exactly the same as yours... so nothing is wrong there...

---

### Post by Elfy on 2008-09-05
Try 

```
cat /etc/sudoers
```

---

### Post by csogilvie on 2008-09-05
this gives me a "permission denied"

I can of course view it just fine if I "sudo cat foo"

---

### Post by yjwong on 2008-09-05
> **csogilvie said:**
> I have not changed anything with my account settings, but now sudo is no longer required to view the logs.

Hmm, I presume that is normal behaviour. I guess "sudo" isn't needed to view the logs. Possibly other members can verify this?

However, I think that normal (non-admin) users will not be able to view the critical log files because they are not in the "adm" group. Correct me if I'm wrong.

---

### Post by csogilvie on 2008-09-05
I am part of the admin group, but what troubles me is that the behaviour has changed today...  and I didn't change anything!

---

### Post by Elfy on 2008-09-05
It doesn't sound like there is anything wrong as long as you can't edit the files without root rights.

You should be able to cat the logs, are you sure you used to need sudo to do so.

---

### Post by csogilvie on 2008-09-05
completely sure!  

My home-system is a mockup of a webserver for work, so I can putter around and not worry about making a mess of a production machine.

---

### Post by Elfy on 2008-09-05
mmm.. well I've never needed to use sudo to view anything other than sudoers - obviously not opened every file but that is the only one I've needed to give root rights to cat for.

---

### Post by csogilvie on 2008-09-05
Ok...  I'm relieved a bit then...  As this is normal behaviour for others.

Perhaps I need some more coffee.

Thank you to all who helped.

---

### Post by Elfy on 2008-09-05
Check your bash history see what commands you've been running, see if you can see anything in the logs.

---

### Post by yjwong on 2008-09-05
Heh, if you're still feeling insecure, you could just change the permissions for the log file (:

---

