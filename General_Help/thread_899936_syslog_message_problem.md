---
title: "syslog message problem"
date: 2008-08-24
forum: General Help
---

### Post by KaneHau on 2008-08-24
Aloha:

I am running Ubuntu 8.04 and am having a problem with syslog.

I want everything that goes to /var/log/syslog to also go to a user named:  steve

The current /etc/syslog.conf  entry for /var/log/syslog is:

*.*;auth,authpriv.none      -/var/log/syslog

I've added this:

*.*;auth,authprov.none     steve

I've also tried:

*.*                                         steve

Of course, I then do a restart (also did 'stop' 'start') of /etc/init.d/sysklogd.

Interestingly, I see the restart message of syslogd to the logged in user (steve). However, I never see any other messages.  Tailing /var/log/syslog  shows many messages (general drivel) that never show up to user 'steve's logged in session.  I've tried other user names, etc... nothing ever appears except the syslogd restart message.

Never had this happen under any other unix's - any help would be greatly appreciated (oh yes... rebooting the server also doesn't change this).

Mahalo!

---

### Post by pauper on 2008-08-24
Separate users with commas: *.*;auth,authprov.none,steve
Try tabs instead of spaces: *.*^I^I^I^Isteve

```
man syslog.conf
```

---

### Post by mssever on 2008-08-24
Why do I get the impression that you're in Hawai‘i? :)

---

