---
title: "Users unable to log in"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by douglaswood34 on 2009-10-21
Okay, not exactly a newbie since I have been using linux for 9+ years now, but I have run into a problem.  I knew better than to upgrade the way I did, but I did it for anyway......  Here is the scoop...

I upgraded from 8.04->8.10-->9.04-->9.10.  Somewhere along the way, all other users have lost the ability to log in.  I have one user currently other than myself.  When I try to log in as that user (username and password correct) from a Gnome Login screen, it starts to load, then kicks me back and asks for a password for my user account.  I have tried to create new users, all do the same.  They start to load, then ask for my password, and log into my account.  I have tried logging in to the other users accounts from a command line, which works fine.  What did I break  I am pretty much tempted to wipe and start over...

---

### Post by Iowan on 2009-10-21
[This]("http://www.psychocats.net/ubuntu/resetpassword") might help (or not).  If you have access to **sudo**, you can check the */etc/passwd* file to see if the users are listed there.

---

### Post by douglaswood34 on 2009-10-24
I am able to log in just fine with my password.  It is when the other user tries to log in, they are sent to log in as me for some reason, as if coming off a locked screen saver after they have entered their username and password.  I tried resetting their password from the administrative tools, but that didn't do any good.  Do I need to do it from single user mode?

---

### Post by douglaswood34 on 2009-10-24
As it turns out, I can't even create a new user account that will work..... I can create one, but they can't log in....  My main user account logs in fine....:confused:

---

