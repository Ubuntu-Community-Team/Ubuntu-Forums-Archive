---
title: "[SOLVED] Non-root shutdown command?"
date: 2008-08-22
forum: General Help
---

### Post by eapache on 2008-08-22
I would like to create a desktop icon that immediately shuts down the computer (rather than bringing up the Suspend-Hibernate-Reboot-Shutdown prompt).

The normal command for this is```
sudo shutdown -h now
```however I don't want to have to type in my password. Since gnome-power-manager (which handles the System->Quit button) can do this without sudo privileges, I'd like to use the same command.

Does anybody know what it is?

---

### Post by WRDN on 2008-08-22
This [How To]("http://ubuntuforums.org/showthread.php?t=134968") may be of some help.

---

### Post by jerome1232 on 2008-08-22
Your questions interests me so far I've pulled from this page [http://osdir.com/ml/gnome.gdm.general/2005-12/msg00010.html](http://osdir.com/ml/gnome.gdm.general/2005-12/msg00010.html)

that gdmflexiserver has something do with it. Now running gdmflexiserver all by itself get's me back to the gdm login screen, there is a -c option, I'm trying to figure out if it can be used to reboot.

That's the closest I've gotten so far.

---

### Post by Rhubarb on 2008-08-22
You could add the shutdown command to your /etc/sudoers file.
Have a look here:
[http://howto.wikia.com/wiki/Howto_allow_non-super_users_to_shutdown_computer_in_Linux](http://howto.wikia.com/wiki/Howto_allow_non-super_users_to_shutdown_computer_in_Linux)

I haven't tried this myself, but it should work.

---

### Post by livestockPimp on 2008-08-22
from the # prompt type "visudo"
in here you adjust sudo privliges.
add a new line as follows:

username     ALL=(ALL) NOPASSWD:/sbin/reboot,/sbin/shutdown

This will allow "username" to perform the commands "reboot" and "shutdown" without a password.

---

### Post by Endolith on 2009-01-08
The Gnome panel can do this without setting any weird sudoers or other things.   How does it do it?

---

### Post by Ahadiel on 2009-01-08
I'd imagine it communicates with gdm (which runs as root).

---

### Post by iaculallad on 2009-01-08
Or simply issuing the command below on your terminal:

```
sudo chmod u+s /sbin/shutdown
```

and from there, you could shutdown as a regular user.

---

### Post by Endolith on 2009-01-08
> **Ahadiel said:**
> I'd imagine it communicates with gdm (which runs as root).

Yeah, I found that gnome-session has stuff like GDM_LOGOUT_ACTION_SHUTDOWN in it, and fast-user-switch-applet has stuff like 

[php]#define GDM_SUP_LOGOUT_ACTION_HALT    "HALT"                /* None */
#define GDM_SUP_LOGOUT_ACTION_REBOOT    "REBOOT"            /* None */
#define GDM_SUP_LOGOUT_ACTION_SUSPEND    "SUSPEND"            /* None */[/php]but I have no idea how this works.  It's all gibberish to me.  I want to send the signal from a python script, and have it do the gnome-session stuff with no shutting down if you still have apps open.  But maybe that's impossible.

---

### Post by Ahadiel on 2009-01-08
Yeah, there most likely are security measures inplace to prevent other applications from using gdm.

---

