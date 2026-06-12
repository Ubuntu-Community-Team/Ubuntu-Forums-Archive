---
title: "logging in as root"
date: 2005-11-07
forum: General Help
---

### Post by Specialsauce on 2005-11-07
how do i log in as root? i need to, but im totally new and i dont know how. i mean, whats the password? it sure isnt the password i detailed on installation......

---

### Post by Sheco on 2005-11-07
You only created a user account, which has access to privileged tasks, with its own password, several GUI apps ask for your password and run internally as root.

on the command line, you have to use sudo, for example:

sudo ls /root

if you want a root shell:

sudo sh

---

### Post by drummer on 2005-11-07
Ubuntu doesn't have a root account by default. To do things as root, run commands with sudo (ie "sudo [command to run as root]") in a terminal, and if running an application, "gksudo [app name]" in the run command dialog (Alt-F2).

Also, if you need a terminal running as root (it sudo isn't working for what you're doing), "sudo su" in a normal terminal will do the trick.

more info here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

EDIT - beat me to it

---

### Post by oskude on 2005-11-07
just for the record

i made a password for root user with this
```
sudo passwd
```
and if i need root user access in long term, i do
```
su -
```

---

