---
title: "need simple help with visudo"
date: 2008-11-30
forum: General Help
---

### Post by maestrobwh1 on 2008-11-30
I am trying to allow myself as a user to not use a password as sudo when using network commands.  It isn't working so if someone could check out in **bold** what I added and fix/comment on it, that would be of great help.

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

[B]# Add wireless commands
brian   ALL=(root) NOPASSWD: /sbin/ifconfig, /sbin/iwconfig, /sbin/dhclient, /sbin/dhclient3, /sbin/pump, /sbin/ifup, /sbin/ifdown[/B]

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
~

---

### Post by drs305 on 2008-11-30
> **maestrobwh1 said:**
> 

[B]# Add wireless commands
brian   ALL=(root) NOPASSWD: /sbin/ifconfig, /sbin/iwconfig, /sbin/dhclient, /sbin/dhclient3, /sbin/pump, /sbin/ifup, /sbin/ifdown[/B]

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
~

Make it look like this. Your entry should be the last one in the sudoers file to ensure it is not overridden by later instructions:
```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

[B]# Add wireless commands
brian ALL = NOPASSWD: /sbin/ifconfig, /sbin/iwconfig, /sbin/dhclient, /sbin/dhclient3, /sbin/pump, /sbin/ifup, /sbin/ifdown[/B]

```

---

### Post by cmay on 2008-11-30
> 
# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALLi would have tried to uncomment this first. i have no man page to check on but it seems like it is written as a help to do exactly this your asking for. 
hope it helps.-

nevermind above post seem to look more right.

---

### Post by maestrobwh1 on 2008-11-30
Perfect!  Works great.

> **drs305 said:**
> Make it look like this. Your entry should be the last one in the sudoers file to ensure it is not overridden by later instructions:
```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

[B]# Add wireless commands
brian ALL = NOPASSWD: /sbin/ifconfig, /sbin/iwconfig, /sbin/dhclient, /sbin/dhclient3, /sbin/pump, /sbin/ifup, /sbin/ifdown[/B]

```

---

