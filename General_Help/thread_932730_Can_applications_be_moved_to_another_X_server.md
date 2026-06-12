---
title: "Can applications be moved to another X server?"
date: 2008-09-28
forum: General Help
---

### Post by SimonHickling on 2008-09-28
I know I can use ```
ssh -X
``` to view the windows from a remote machine.

Is it possible to start an app on one machine and at some point in the future get the windows sent to a different machine (like they are with ssh -X) without restarting the app?

---

### Post by rocketssss on 2008-09-28
I'm interested in this as well, as I have a [similar thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=932589") open about having X apps open when I SSH and having them stick around after closing my SSH tunnel.

I wonder if there is a way to start an X server that just always hangs around for a particular user rather than instantiated on demand.

---

### Post by cariboo on 2008-09-28
I believe you can use screen for what you want to do. Check:

```
man screen
```

Jim

---

### Post by SimonHickling on 2008-09-28
As I understand it the PC you have the GUI on *is* the server.  The app at the other end of the ssh tunnel is the client.  I have posted a reply on your thread.  If I can help further just ask.

---

### Post by SimonHickling on 2008-09-28
Thanks, screen is great for non X apps.  but I'm after something similar for X-based apps.  For instance I can log into my desktop start firefox, browse to a site.  Then later while firefox is still running on the desktop, I log into my laptop, ssh into the desktop and redirect the firefox window onto the X server on the lapto.

---

### Post by mindoms on 2008-09-28
> **SimonHickling said:**
> Thanks, screen is great for non X apps.  but I'm after something similar for X-based apps.  For instance I can log into my desktop start firefox, browse to a site.  Then later while firefox is still running on the desktop, I log into my laptop, ssh into the desktop and redirect the firefox window onto the X server on the lapto.

I guess xmove can do the job. i just played around a bit but it doesnt work yet.

Maybe you, or somebody else can get this up and running. please post any results here.
[http://fixunix.com/xwindows/91803-xmove-ssh.html](http://fixunix.com/xwindows/91803-xmove-ssh.html)

btw. if you want to keep programs running after terminating your ssh session start the app with
```
nohup APP &
```
(no hang up)

hth, stefan

---

### Post by SimonHickling on 2008-09-29
Xmove looks to be what I'm looking for -thanks.  If I get any joy with it I'll post my experiences here.

---

