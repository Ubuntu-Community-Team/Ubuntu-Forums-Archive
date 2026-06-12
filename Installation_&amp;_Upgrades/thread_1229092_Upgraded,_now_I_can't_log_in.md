---
title: "Upgraded, now I can't log in"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by sketerpot on 2009-08-01
I upgraded to Jaunty recently, using the default Gnome configuration, and now whenever I start up, the login screen won't let me pass. Here's what happens:

1. The login screen comes up.

2. I enter my username and password, as usual.

3. The login screen asks for my username again, as if nothing had happened. This goes on forever.

If I enter the wrong username or password, the login screen tells me that I've got the wrong password. But if I type them in correctly, it just repeats the question.

This happens no matter what session type (Gnome, KDE, Failsafe Terminal, etc.) I choose.

Any suggestions?

---

### Post by alexandari on 2009-08-01
well,you might try logging in as root and figuring out the problem
hit ctrl+alt+f4
login as root
then **killall gdm**
after which **startx**

---

### Post by ajgreeny on 2009-08-01
> **alexandari said:**
> well,you might try logging in as root and figuring out the problem
hit ctrl+alt+f4
login as root
then **killall gdm**
after which **startx**
But you can't login as root as the root account is disabled by default in ubuntu.  It is possible to do so if you set the system up in that way, but most people will not have done so.

So reboot into recovery mode then look to see if you have your username correct when you login, ```
ls /home
``` and the users will be listed.  If that is correct try a new password with ```
passwd username
```and enter the new onw twice as asked, and then try rebooting and logging in again.

---

### Post by sketerpot on 2009-08-01
My username and password are set correctly; I know this because I can press Ctrl-Alt-F4 to get a text-only terminal and log in as normal. And while I can't log in as root, I can log in as myself and use sudo.

I'll try out the approach of killing gdm and running startx; maybe that will turn up some error messages.

---

