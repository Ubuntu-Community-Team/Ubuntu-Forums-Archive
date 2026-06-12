---
title: "&quot;sudo&quot; dont works"
date: 2008-08-12
forum: General Help
---

### Post by Trimax on 2008-08-12
Im having a lot of problems starting gnome (gdm-settings-daemon) and I need use the TTY but "sudo" command hangs every time I want to use it.

Its never ask me for password. 

I type the command (for example: "sudo ifup wlan0") and nothing happends.  It dont response ctrl+z nor ctrl+c.  Then I go to other TTY and try to kill the process, but sudo dont works.

Please help me!!

---

### Post by Crafty Kisses on 2008-08-12
Try the following:
```
sudo svnadmin dump /usr/local/svn/project >  sudo /usr/local/backup/svn/repo.dump
```

---

### Post by Uchiha_madara on 2008-08-12
Are you working under network

or :

you are the administrator or not ?

if you are working under network

sudo well be disabled because sudo is an Administrator command

---

### Post by Trimax on 2008-08-14
- When the bug comes the sudo dont response, then any "sudo" command **neither**.  In order to try anythin, I did this in a LiveCD boot and this is the results:
```
ubuntu@ubuntu:~$ sudo svnadmin dump /usr/local/svn/project >  sudo /usr/local/backup/svn/repo.dump
sudo: svnadmin: command not found
ubuntu@ubuntu:~$ 

```

- There isnt any network.  I just installed Ubuntu 8.04.1.  When I reboot 1st time the "avahi-daemon" FAIL, then desktop login freezes (I tryed Gnome and KDE, both freeze).

---

