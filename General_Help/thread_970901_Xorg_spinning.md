---
title: "Xorg spinning"
date: 2008-11-04
forum: General Help
---

### Post by kpgalligan on 2008-11-04
I have a long running process running on a desktop machine.  I'm currently logged in via ssh and managing the instance over the command line.  However, I notice when running top that xorg is consuming large amounts of CPU.  Up to 99-100%.  Nobody has been logged into this machine since it was rebooted (from the graphical login).  Something weird is going on.  For now, however, I'm wondering if I can just kill xorg so my process will run faster and figure out what's wrong later.  Thoughts?  I don't want to mess up the long running process, as its going good so far, but xorg is eating 1/4 or the system resources (Quad-core machine).

---

### Post by Coreigh on 2008-11-04
Is the long running process you mentioned using a GUI? Was it started via ssh/cmdln, or did you log in to the desktop start the process and then continue managing it from ssh?

If the process was started in a GUI then killing X might abort the process.

If that is NOT the case you can restart X or even kill the display manager and X.

There is a *right* way to do that but alas I do not know the *right* way.

Update.
This was suggested from a result in a google search for stop x server:
```
sudo /etc/init.d/gdm stop
```

---

### Post by kpgalligan on 2008-11-04
The machine was rebooted, after which, all logins have been via ssh.  I started the long running process over ssh with 'nohup [the process] &', so it should run until something physically bad happens to the box.

Could I just run 'kill [pid]' on xorg?

---

### Post by kpgalligan on 2008-11-04
For the curious, I did...

sudo /etc/init.d/gdm stop

Everything looks OK...

---

