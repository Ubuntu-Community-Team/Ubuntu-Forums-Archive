---
title: "Crashplan Installation"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by DarKnyht on 2009-06-24
I have installed CrashPlan on my ubuntu laptop so that I can do regular backups of my data.  I got the software installed without difficulty, but I have run into something that I cannot figure out.  There is a server application that needs to run as root the command is:

```
/etc/init.d/crashplan start
```

I can easily start it once I am logged in from a terminal window, however I want the command to run automatically at boot.  The instructions state the following:
> 
The background service, now called 'CrashPlan' which starts the
backup engine, will be installed and setup to run from your designated
directory. If defaults are used, it will be:

/etc/init.d/crashplan

and it will be linked from:

/etc/rc2.d

Note that on some flavors of Linux you may need to added the following to /etc/init.d/boot.local:

/etc/init.d/crashplan start

However, after doing both these suggestions the service does not start automatically.  Can anyone help point me to what I really need to do in order to get this working?  I really like the crashplan software since it lets me backup locally and to my parent's Vista machine far away (and let them do the same).

Thanks in advance for the assistance.

---

### Post by garretwp on 2009-06-29
I have read from the crashplan site that this is known issue and they are working on a fix. For the time being, when you reboot your machine, you will have to run it manually.

- Garrett

---

### Post by CDrewing on 2011-09-22
> **DarKnyht said:**
> However, after doing both these suggestions the service does not start automatically.  Can anyone help point me to what I really need to do in order to get this working?  I really like the crashplan software since it lets me backup locally and to my parent's Vista machine far away (and let them do the same).

Thanks in advance for the assistance.

Is this the reason why Crashplan is working perfectly at first run right after install but fails to connect after having a reboot? (That's my problem actually)

Rgds
Christian

---

### Post by CDrewing on 2011-09-22
**HAH!**

A simple *sudo service crashplan start* and Crashplan is running as if it never has been making problems before.

OK, so to make it working generally I will have to go into init.d as described above. 

Thank you!

---

