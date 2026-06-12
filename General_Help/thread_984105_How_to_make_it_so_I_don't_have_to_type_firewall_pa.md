---
title: "How to make it so I don't have to type firewall password at startup?"
date: 2008-11-16
forum: General Help
---

### Post by josephellengar on 2008-11-16
I like having the icon in the notificatoin area.  It makes me feel more comfortable.  Lol.  Yeah, I still have some of the windows mindset.
Here is my sudoers, if that helps:
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

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by drs305 on 2008-11-16
Since you posted your sudoers file, here is a method to run a command without having to type in the password by editing sudoers. This entry will allow you to start an app without needing to enter the password for sudo. I won't comment on security issues, just present the way to do what you suggested. There are other methods of starting commands *during boot* by placing them in the applicable /etc/init.d folder.

In this instance, I am going to start 'gufw' (gnome uncomplicated firewall), which normally needs a password to start. The run command for gufw is "/usr/share/gufw/gufw.py"

I have added Cmnd_Alias TEST. You can name it whatever you wish.
```

# Cmnd alias specification
Cmnd_Alias TEST = /usr/share/gufw/gufw.py

```
Then, add this *as your last line*. Of course, substitute your username:
```

*username* ALL=(ALL) NOPASSWD: TEST

```

---

