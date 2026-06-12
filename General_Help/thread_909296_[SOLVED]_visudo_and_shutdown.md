---
title: "[SOLVED] visudo and shutdown"
date: 2008-09-03
forum: General Help
---

### Post by desmane on 2008-09-03
Hi people, 

I'd like to shutdown my computer via Kcron job, but when I type sudo shutdown -h now, or sudo halt/reboot it still ask me for a password. 

this is my /etc/sudoers file: 

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification
#Cmnd_Alias SYSTEM = /sbin/shutdown, /sbin/halt, /sbin/reboot, /sbin/poweroff

# User privilege specification
root	ALL=(ALL) ALL
%admin ALL = (ALL) NOPASSWD:/sbin/shutdown -hP now

# Members of the admin group may gain root privileges

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

As you can see, I've tried other stuff too (username: andi/%admin, Cmnd Alias etc) but nothing worked. 

I am running Kubuntu 8.04, KDE 3.59
Linux andibuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


nothing helped: 
[http://www.staschke.de/linux/shutdown.html](http://www.staschke.de/linux/shutdown.html)
[http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/](http://linux.byexamples.com/archives/315/how-to-shutdown-and-reboot-without-sudo-password/)

There must be a solution ey?

ThXX!

---

### Post by tuxxy on 2008-09-03
Have you tried Kshutdown or must it be Kcron

---

### Post by desmane on 2008-09-05
Yeah, I'd like to use the halt / shutdown -h command because it shuts down my computer immediately (kaffeine for example ask for confirmation) and kshutdown doesn't manage to quit kdm properly.

---

### Post by desmane on 2008-09-05
I figured it out, you have to restart x. ](*,)
this is how it looks like: 
```

# User privilege specification
root	ALL=(ALL) ALL
username	ALL=NOPASSWD: /sbin/halt
# Members of the admin group may gain root privileges
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

but still doesnt work after I restsart the computer. But is wrong here? Anybody? 
Should I dpkg reinstall something do make it work?

---

### Post by chrisrco on 2008-09-15
I had the same problem (seemed to work but didn't after restarting the computer).  I was getting very frustrated that the normal suggestions were simply not working.  I found that putting the NOPASSWD line at the end of the sudoers file worked.  Mine currently is:
```


# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

username ALL = NOPASSWD: /sbin/poweroff

```

I have no idea why this worked, and I just stumbled up on by copying another sudoers file I found posted somewhere.  Hopefully this was actually the change that got my setup working, and not some other random thing :)  Good luck

---

### Post by desmane on 2008-11-29
thx!!

---

