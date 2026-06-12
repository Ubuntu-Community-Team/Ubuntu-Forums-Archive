---
title: "What runlevel when logging out?"
date: 2008-10-27
forum: General Help
---

### Post by Shardsofmetal on 2008-10-27
In Ubuntu, what runlevel does the machine go into when logging out (not shutting down or restarting, just logging out)? I have a script that runs in runlevels 0 and 6, but the script does not run when I just log out. Thanks

---

### Post by Sam on 2008-10-27
Ubuntu is always in runlevel 2 (except 0 and 6).


BTW, to find out the runlevel, run```
runlevel
```

---

### Post by koenn on 2008-10-27
if your trying to run a log out script, look in /etc/gdm/PostSession/

runlevel 6 is only entered when you're going to rebooting, and 0 is for shutdown

---

### Post by Shardsofmetal on 2008-10-27
will anything in that directory run, or just the Default file?

---

### Post by koenn on 2008-10-28
Don't remember. You could just try ...
A not so bad compromise would be to add scripts to the directory and call them from "Default" if it turns out the don't run by themselves.
In any case, you probably need to set them executable.

---

