---
title: "[SOLVED] CONSTANT hard drive activity"
date: 2008-10-22
forum: General Help
---

### Post by shingalated on 2008-10-22
My hard drive LED is flashing constantly and it the drive is clicking like it is being accessed about 5 times a second.  kjournald is to the top when I use the top command, but that is only using 4%.  I shut off the swap partition and it stopped clicking for 5 or 10 seconds and then it resumed.  Any ideas of what's going on?  It doesn't seem like very healthy behavior.

---

### Post by geirha on 2008-10-22
Hard to say what it could be. Try tailing the logfiles and see if there's something logging alot of activity
```
tail -f /var/log/*.log
```

---

### Post by shingalated on 2008-10-22
Nothing unusual in any of the log files :(

---

### Post by rgerhards on 2008-10-22
Do you have a lot of logging going on? I remember one case where such excessive hard disk usage was caused by the syslogd running in sync-file mode receiving messages at a moderate-to-large pace...

Rainer

---

### Post by jnorthr on 2008-10-22
Loading ubuntu 8.10 beta, i found that turning off the system messages helped a lot. It may not be the major cause of your troubles, but it will help. 
Go to System>Admin>Services until you see Computer Activity Logger klogd and below that is the sysklogd. These abckground daemons will stop if you uncheck these boxes. You may need to click 'Unlock' button first to enter your Authentication password.

I would not turn off the swap file option as this is the only place ubuntu has to store temporary work while running.  Doing so on my system causes it to run r-e-a-l-l-y s-l-o-w

---

### Post by shingalated on 2008-10-22
There is hardly any logging.  It is just your average desktop running MythTV and a verlihub server.  IT has 768MB of RAM.

---

### Post by rgerhards on 2008-10-22
> **jnorthr said:**
> Loading ubuntu 8.10 beta, i found that turning off the system messages helped a lot. It may not be the major cause of your troubles, but it will help. 
Go to System>Admin>Services until you see Computer Activity Logger klogd and below that is the sysklogd. These abckground daemons will stop if you uncheck these boxes.

The bottom line is that this will cause loss of any information you may need to troubleshoot. Most often, the real cause of unnecessary i/o is that sysklogd by default syncs after each write. And it is easy to avoid that. Go to /etc/syslog.conf and check for all filename. For example, you may have

*.* /var/log/somefile

In that format, it syncs. Replace it with

*.* -/var/log/somefile

Note the dash in front. That means "do not sync". With today's hardware, that is not a problem. On many systems, it saves considerable I/O.

---

### Post by shingalated on 2008-10-22
The log files already had the -/var/log... entries all except for the mail logs, but I am not running any mail servers on this computer

---

### Post by rgerhards on 2008-10-22
Well, I guess I am on the wrong path.. Just to make sure, could you temporarily disable sysklogd/klogd and see if that changes anything?

---

### Post by shingalated on 2008-10-22
I tried disabling them from the services dialog, and that did not seem to have any effect.

---

### Post by shingalated on 2008-10-22
It was MythTV I killed the backend for that and now it is fine.
Thanks

---

### Post by meinzy on 2009-03-02
I've had the same problem with constant disk activity.  I've searched multiple posts for hours trying to fix.  No avail.  Then I noticed that when I put a disk in my DVD player it stopped.  I have no idea why.  I now keep a blank cd in my DVD player for a workaround till someone finally fixes this bug.  Hope this jury-rig helps.

---

### Post by mtbdrew on 2009-04-29
Well neither of those things works for me, still have the constant activity.

---

### Post by mtbdrew on 2009-07-09
Still having the same issue, even rolled back to 8.10 due to other issues and still can't get the hard drive activity to settle down.
Any advice would be welcome at this point.

---

