---
title: "shutdown, reboot, without root privileges?"
date: 2008-10-19
forum: General Help
---

### Post by chris4585 on 2008-10-19
the title nearly says it all, the situation is, I'm using openbox, and I've followed [this]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/") guide, and got no luck.

added

ALL     ALL=NOPASSWD:/sbin/shutdown

to /etc/sudoers and still needs a password to run the shutdown command, I'm suspecting that the line is faulted some how.. or maybe I'm not understanding what the line is suppose to do, doesn't it give all users the ability to run that command with no password what so ever?

---

### Post by jerome1232 on 2008-10-20
Well I did it differently but this worked for me (I used apt-get because I didn't want to reboot everytime I tested it)
```
%aptget ALL = NOPASSWD: /usr/bin/apt-get
```

followed by sudo -k, then sudo apt-get update resulted in a passwordless apt-get update. (%aptget would be a new group I created, any1 that needs this passwordless access must be in the group aptget)

edit: using ALL ALL wasn't working for me that's why I did the group.


second edit: ALL ALL = NOPASSWD: /usr/sbin/visudo also works for me, this is placed at the very end of my visudo file. I think it might just be that you have no space after your ':'

last edit:
This ought to do it.
```
ALL ALL = NOPASSWD: /sbin/shutdown, /sbin/reboot
```

---

### Post by chris4585 on 2008-10-20
thank you, your post helped!  I think my problem was not putting the line at the end of /etc/sudoers

---

### Post by chris4585 on 2008-10-21
ok your post did help but I have another problem...

So I thought what I wanted to do was simple, I want to stop NetworkManager before running the shutdown command (I'm doing this within a script).  because when I shutdown I get errors from NetworkManager, because apparently NetworkManager needs hal and dbus to shutdown, but they shutdown before NetworkManager..

so I tried to add to sudoers 
```

ALL ALL = NOPASSWD: /usr/bin/killall
```

to killall NetworkManager, but then i need root privileges.. 

or anyone know a work around to stop NetworkManager from displaying these errors?

---

### Post by p_quarles on 2008-10-21
Network manager will shut off, at the very least, when the computer powers off. Apart from that, I don't see why it would need dbus or HAL to shut off separately, although it may use these things to listen for shutdown signals coming from a display manager (which you are obviously not using). 

In other words, I don't think you ought to be concerned about the errors you are getting from the shutdown process. Unless something is not starting back up correctly, you should not need to do anything special. In any case, "killall" would not be the right command to use in a shutdown script.

---

### Post by chris4585 on 2008-10-21
> **p_quarles said:**
> Network manager will shut off, at the very least, when the computer powers off. Apart from that, I don't see why it would need dbus or HAL to shut off separately, although it may use these things to listen for shutdown signals coming from a display manager (which you are obviously not using). 

In other words, I don't think you ought to be concerned about the errors you are getting from the shutdown process. Unless something is not starting back up correctly, you should not need to do anything special. In any case, "killall" would not be the right command to use in a shutdown script.

Well, I'm making a liveCD, and its not me who cares about the errors for I do know that they are nothing bad, but for the users that might not leave a good impression.  I tried usplashy.. that didn't really work either, just showed the errors then showed the splash screen for a second.  I might just accept I won't get that fixed then.

---

