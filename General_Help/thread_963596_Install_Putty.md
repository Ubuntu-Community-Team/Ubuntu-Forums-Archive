---
title: "Install Putty"
date: 2008-10-30
forum: General Help
---

### Post by Lagerkvist on 2008-10-30
Hello!

I am a noob on Linux and i will have a counter-strike server in the futiuos. But i can't install Putty. And i can't login as root. Pleas tell me who is wrong.

Thanks!

---

### Post by stevek42 on 2008-10-30
1.  Root is not supported in the traditional sense on Ubuntu.  While you can enable the root account, it is more recommended that you use the 'sudo' command to run root scripts.  For instance:  sudo gedit /etc/hosts

If you need to, you can:  sudo su -

2.  Why use putty?  You've got ssh at the command line.  If you really want putty, however, you can install it in Synaptic or with the following command:  sudo apt-get install putty

---

### Post by amedac on 2008-10-30
You don't need to login as root. Just open terminal and type:

```
sudo apt-get install putty
```

---

### Post by Lagerkvist on 2008-10-30
> **amedac said:**
> You don't need to login as root. Just open terminal and type:

```
sudo apt-get install putty
```

Thanks.

But i question. Where is the putty now? After the install.

---

### Post by Titan8990 on 2008-10-30
Use this command:

whereis putty


Most likely it is in your $PATH variable so to launch it:


putty

---

### Post by bytor4232 on 2008-10-30
> **stevek42 said:**
> 2.  Why use putty?  You've got ssh at the command line.  If you really want putty, however, you can install it in Synaptic or with the following command:  sudo apt-get install putty

That was my first thought, however:  

[quote=apt-cache show putty]
Description: Telnet/SSH client for X
 This is the Unix port of the popular Windows ssh client, PuTTY. It supports
 flexible terminal setup, mid-session reconfiguration using Ctrl-rightclick,
 multiple X11 authentication protocols, and various other interesting things
 not provided by ssh in an xterm.
[/quote]

He either likes really likes putty, or needs it to accomplish his counter strike thing.  Obviously it does things other ssh+xterm clients don't.

Doesn't make me run out and apt-get install putty, but hey, to each his own.

---

