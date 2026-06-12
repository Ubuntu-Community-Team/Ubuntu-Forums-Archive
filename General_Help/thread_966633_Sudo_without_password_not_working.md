---
title: "Sudo without password not working?"
date: 2008-11-01
forum: General Help
---

### Post by mosquitogang201 on 2008-11-01
I'm trying to write a script to suspend my computer when I press the sleep key, but I can't figure out how to run the script without entering a password. Sudo is working for everything else, the script works when I enter a password, and my script is /home/daniel/.suspend

Here is /etc/sudoers

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
daniel  ALL=(ALL) ALL
daniel  ALL=NOPASSWD:   /home/daniel/.suspend

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


And this is what I get when I try to run

daniel@ubuntu:~$ sudo /home/daniel/.suspend
[sudo] password for daniel:

Anyone know how to make this work?

---

### Post by geirha on 2008-11-01
The order of the lines makes a difference. The line starting with %admin overrides your two lines for the daniel user. Also, if the user daniel is a member of the admin group, then the line «**daniel ALL=(ALL) ALL**» is redundant, so remove it. And put the line «**daniel ALL=NOPASSWD: /home/daniel/.suspend**» below the %admin-line and it should work as expected.

---

### Post by mosquitogang201 on 2008-11-01
Alright that was the problem. Since I'm the only user I commented out the last admin line and everything is working now. Thanks!

---

