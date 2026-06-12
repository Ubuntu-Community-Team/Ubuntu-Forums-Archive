---
title: "set shutdown but to &quot;shutdown now&quot;"
date: 2008-09-06
forum: General Help
---

### Post by nlz on 2008-09-06
When I hit the power-off button of my computer, the screen pops up which gives you the choice to power-off, log-out, etc. But i want the computer to shut down gracefully if i press it (so that it gives the 'shutdown now' commmand with SU priviliges).

(I want this so I can run a archiving/backup/filesharing PC without a monitor)

---

### Post by Elfy on 2008-09-06
I thought there was an option on the powere management in system preferences. It defaults to ask me - I thought there was a shutdown option.

Can't look without logging into gnome :)

---

### Post by hardyn on 2008-09-06
system > preferences > power management > general > actions

---

### Post by desmane on 2008-09-06
Try

sudo apt-get install kpowersave

it gives you options on how to behave when pressing the power button. 

If you have a "sleep button" on your keyboard, you could use that as well. Apply a custom command (like "sudo halt" or "sudo shutdown -h 1") and edit the /etc/sudoers file. 

Type: 

```
sudo visudo
``` and add the following line:

```
yousername	ALL=NOPASSWD: /sbin/halt
```

that it looks like this: 

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
# User privilege specification
root	ALL=(ALL) ALL
username	ALL=NOPASSWD: /sbin/halt
# Members of the admin group may gain root privileges
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

so you don't have to be root using this command. 

In Visudo, move to the line you want to edit and then press "insert", press escape and type :wq to save and quit. 

Restart X

---

### Post by iaculallad on 2008-09-06
Yes, you could configure that on the Power Management Preferences (System->Preferences->Power Management), under "General" tab to be exact.

---

### Post by nlz on 2008-09-08
thanks!

---

### Post by Washer on 2008-09-08
visudo is a bitch to deal with. I prefer doing it in gedit
```

export EDITOR=gedit
sudo -E visudo
```

---

