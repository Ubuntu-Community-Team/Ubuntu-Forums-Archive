---
title: "I want all privlages now!!!"
date: 2008-11-14
forum: General Help
---

### Post by wildman4god on 2008-11-14
I am sick of ubuntu telling me I can't do stuff, I want to know how to give myself all privlages, I don't want a lecture on its not safe, I own the computer and right now I know better than it, especially when these privlages things are keeping me from installing hardware. So how do I give myself all privlages, can anyone help me?

---

### Post by taurus on 2008-11-14
```
sudo su
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Titan8990 on 2008-11-14
Well, you would have two options. One, is to log in as root. It is against forum policy to tell you how to do so. I will explain how to remove the password prompt when using sudo.

First, lets look at the /etc/sudoers file:

```
jordan@einstein:~$ sudo cat /etc/sudoers 
[sudo] password for jordan:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


We want to change: 

%admin ALL=(ALL) ALL

to:

%admin ALL=NOPASSWD: ALL

To do this use the following command:


sudo visudo

You will no longer get a password prompt when using sudo commands.


Hope that helps.

---

### Post by issih on 2008-11-14
If you are that determined, despite knowing all the risks, then I'd recommend migrating to a distribution that allows you to run as root. Something that Ubuntu deliberately makes complicated.

Hope that helps

---

### Post by Titan8990 on 2008-11-14
I agree with Issih. Distros such as Slackware start you out with only a root account.

---

